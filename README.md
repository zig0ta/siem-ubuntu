# siem-ubuntu
#Updating our system
sudo apt update
sudo apt upgrade

#UFW setup
sudo ufw allow ssh
sudo ufw allow 9200/tcp #Elasticsearch HTTP
sudo ufw allow 9300/tcp #Elasticsearch Transport
sudo ufw allow 5601/tcp #Kibana
sudo ufw allow 5044/tcp #Logstash Beats input (if Filebeat is used)
sudo ufw enable

sudo ufw status

#JDK install
sudo apt install openjdk-17-jdk
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg

#Elastic add repo
sudo apt-get install apt-transport-https
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/9.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-9.x.list
sudo apt-get update && sudo apt-get install elasticsearch
