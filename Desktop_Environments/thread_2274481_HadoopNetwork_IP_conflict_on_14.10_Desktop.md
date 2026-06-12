---
title: "Hadoop/Network IP conflict on 14.10 Desktop"
date: 2015-04-20
forum: Desktop Environments
---

### Post by anand14 on 2015-04-20
Hi All:

I have installed Hadoop2.6.0 and Java 1.7.0_75 and trying to start Hadoop daemons when I get a connection refused error, and when I check the related wiki page, they say it has got to do with Network. Please find below

/home/anand_vihar
anand_vihar@Latitude-E5540:~$ cd hadoop-2.6.0
anand_vihar@Latitude-E5540:~/hadoop-2.6.0$ . .hadoop
/home/anand_vihar/hadoop-2.6.0
/home/anand_vihar/jdk1.7.0_75
/home/anand_vihar/hadoop-2.6.0
anand_vihar@Latitude-E5540:~/hadoop-2.6.0$ start-dfs.sh
Starting namenodes on [localhost]
localhost: starting namenode, logging to /home/anand_vihar/hadoop-2.6.0/logs/hadoop-anand_vihar-namenode-Latitude-E5540.out
localhost: starting datanode, logging to /home/anand_vihar/hadoop-2.6.0/logs/hadoop-anand_vihar-datanode-Latitude-E5540.out
Starting secondary namenodes [0.0.0.0]
0.0.0.0: starting secondarynamenode, logging to /home/anand_vihar/hadoop-2.6.0/logs/hadoop-anand_vihar-secondarynamenode-Latitude-E5540.out
anand_vihar@Latitude-E5540:~/hadoop-2.6.0$ hdfs dfs -ls
ls: Call From Latitude-E5540/127.0.1.1 to localhost:9000 failed on connection exception: java.net.ConnectException: Connection refused; For more details see: ** [http://wiki.apache.org/hadoop/ConnectionRefused](http://wiki.apache.org/hadoop/ConnectionRefused)**

Now on that website


[h=1]Connection Refused[/h] You get a  ConnectionRefused Exception when there is a machine at the address  specified, but there is no program listening on the specific TCP port  the client is using -and there is no firewall in the way silently  dropping TCP connection requests. If you do not know what a TCP  connection request is, please consult the [specification]("http://www.ietf.org/rfc/rfc793.txt"). 
Unless there is a configuration error at either end, a common cause for this is the Hadoop service isn't running. 
This  stack trace is very common when the cluster is being shut down -because  at that point Hadoop services are being torn down across the cluster,  which is visible to those services and applications which haven't been  shut down themselves. Seeing this error message during cluster shutdown  is not anything to worry about. 
If the application or cluster is not working, and this message appears in the log, then it is more serious. 

[LIST=1]
[*]Check the hostname the client using is correct 
[*]Check the IP address the client is trying to talk to for the hostname is correct. 
[*]Make  sure the destination address in the exception isn't 0.0.0.0  -this  means that you haven't actually configured the client with the real  address for that 
[/LIST]
service, and instead it is picking up the server-side property telling it to listen on every port for connections. 

[LIST=1]
[*]**Check that there isn't an entry for your hostname mapped to 127.0.0.1 or 127.0.1.1 in /etc/hosts (Ubuntu is notorious for this) **
[*]Check the port the client is trying to talk to using matches that the server is offering a service on. 
[*]On the server, try a telnet localhost <port> to see if the port is open there. 

[*]On the client, try a telnet <server> <port> to see if the port is accessible remotely. 

[*]Try connecting to the server/port from a different machine, to see if it just the single client misbehaving. 
[*]If  you are using a Hadoop-based product from a third party, including  those from Cloudera, Hortonworks, Intel, EMC and others -please use the  support channels provided by the vendor. 
[*]Please do not file bug reports related to your problem, as they will be closed as [Invalid]("http://wiki.apache.org/hadoop/InvalidJiraIssues") 

[/LIST]
None of these are Hadoop problems, they are host, network and firewall configuration issues. As it is your cluster, [only you can find out and track down the problem.]("http://wiki.apache.org/hadoop/YourNetworkYourProblem")

[B]If I remove all hadoop folders (uninstall) and once again install, it seems to work. However, after a couple of start and stop of daemons, the problem recurrs. Can anybody here advise or point me to the right forum.

Thanks

Regards,

Anand[/B]

---

### Post by dino99 on 2015-04-20
that error is quite common:
[http://stackoverflow.com/questions/25708502/hadoop-standalone-installation-java-net-connectexception-connection-refused-e](http://stackoverflow.com/questions/25708502/hadoop-standalone-installation-java-net-connectexception-connection-refused-e)
[http://askubuntu.com/questions/352868/i-cant-connect-to-hadoop-port-9000](http://askubuntu.com/questions/352868/i-cant-connect-to-hadoop-port-9000)

---

