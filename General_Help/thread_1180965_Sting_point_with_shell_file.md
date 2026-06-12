---
title: "Sting point with shell file"
date: 2009-06-07
forum: General Help
---

### Post by ml41782 on 2009-06-07
Hey everyone. 
I have a sticking point that I can't seem to get around. 
I'm running minicom and dumping a capture to a text file. I tail the file for what I want. What I wanted to do was to kill the process, delete the text file once a week and restart the process all over again. 
 
The problem is that I can't seem to make it work successfully unattended or attended. 
 
The login that I use has full rights to the directory in which it is running. I can kill the capture file  no problem. 
 
The directory owner id is the one executing the commands. 
 
I start minicom using this format 
 
 
minicom -C well_data.txt
 
 
stop and remove the text file..
 
 
 well_stop.sh  
 
 #!/bin/bash
# well_stop.sh
# created 1 jun 2009
#
pkill minicom
rm /home/otg1017/well_data.txt
# eof
 
My restart is just as simple
 
#!/bin/bash
# wel_start.sh
# created 1 june 2009 
#
minicom -C well_data.txt
# eof

---

### Post by blueridgedog on 2009-06-07
What errors do you get when you run the two scripts manually?  The second script needs a full path to the well_data.txt file so when run from cron (I assume that is what you have doing once a week execution) it knows where the file is.

---

### Post by ml41782 on 2009-06-07
since the file has started as a cron job I dont see any error messages. I just haven't seen it restart the next day.  pkill does its job and minicom stops. 
 
I setup the capture location in the default minicom startup location. 
 
I was never able to locate any other welldata files on the system. 
 
Where else can I look for errors messages ? I'm not traying to be smart. I have used linux flavors on an off for 10 years and always ended up back at microsoft ( YUCK )  I have been on this project now for 6 months and I'm not looking back :)
 
WIth that said I'm still learning. my background is web servers and network engineering. It also covers a strong RF background. 
 
Mike

---

### Post by blueridgedog on 2009-06-07
Is the job in your crontab or the systems?  If it is the systems, It may have trouble knowing where to write the file.

---

### Post by ml41782 on 2009-06-07
The scripts are in the crontab of otg1017
 
23 59 * * *   /home/otg1017/welstop.sh
0    0 * * *    /home/otg1017/welstart.sh

---

### Post by ml41782 on 2009-06-07
The file names do match I goofed when I typed them in here in the forum. I did verify that before hand. 
 
mike

---

### Post by blueridgedog on 2009-06-07
The cron entries look fine, are the two scrips executable?

---

### Post by ml41782 on 2009-06-07
yes permissions are 755 on both. 
 
Something for another day. 
 
Thank you 
good night

---

