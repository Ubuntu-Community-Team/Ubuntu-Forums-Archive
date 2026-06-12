---
title: "I can't get utorrent server working please could someone help?"
date: 2012-01-17
forum: Desktop Environments
---

### Post by davegurn on 2012-01-17
Hi let me start by saying i have read all the help documentation first and searched around before posting.

Basically i have followed these instructions

1. Download  utorrent to your home folder. Right click the downloaded file  (Eg:utorrent-server-3.0-25053.tar.gz), click 'Extract here'
2. You will get a folder called utorrent-server-v3_0 in the same folder as the downloaded file. Open the folder.
3.  Right click the file 'utserver' and make it executable by following  this step .. right click on utserver > properties > permissions  > add tick on Allow executing file as program > close it
4. Run the file 'utserver' by double clicking it.
5. Nothing happens. It's alright. utserver is running as a background program.
6- open your browser like firefox , chrome , opera ... etc 
7- type in URL : [http://localhost:8080/gui/](http://localhost:8080/gui/)   
8- username: admin 
   no password


But when i go to [http://localhost:8080/gui/](http://localhost:8080/gui/) or [http://myip:8080/gui/](http://myip:8080/gui/) recieve this message


The µTorrent WebUI does not seem to be installed. Click [here]("http://localhost:8080/gui/download_webui") to try to install it, or see the [guide]("http://utorrent.com/webui-guide.php") for more details.


I have made sure utserver is executable and that webui.zip is in the utserver folder with the .dat files but it still wont work!


When i run utserver from terminal i recieve this log


~/Downloads/utorrent-server-v3_0$ ./utserver
server started - using locale C
Using locale C
GetNodeID failed, using /dev/random
total physical memory -1 max disk cache 33554432
File not found during integrity check: ./dht.dat
File not found during integrity check: ./dht.dat.new
File not found during integrity check: ./dht.dat.old
File not found during integrity check: ./rss.dat
File not found during integrity check: ./rss.dat.new
File not found during integrity check: ./rss.dat.old





My goal is to be able to use utorrent gui anyone know what im doing wrong please.


Thanks in advance for any help


Oh yeah im trying to install it on a vps through lxde using vncviewer if thats relevant.

---

### Post by davegurn on 2012-01-17
Never mind ive been banging my head againt the wall for no reason, i never knew about the amazing program called wine :)

---

