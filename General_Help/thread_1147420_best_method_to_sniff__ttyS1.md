---
title: "best method to sniff  ttyS1"
date: 2009-05-03
forum: General Help
---

### Post by ml41782 on 2009-05-03
Good afternoon, 

I didn't have this problem before. 
I need to pull a snippet of data from a constant data stream every 5 minutes. I dont want to leave a program running full time on this port. 

what I have done in the past and I dont like it is this. 

cat /dev/ttyS1 > weldatdanow.txt 

then 

tail -n2 weldatanow.txt > datanow.txt  from here I  bring the data into the web page. 

Problem. the cat command on the serial port is processor intense. I dont want it running any longer than a minute maybe 2 every 5 to 10 minutes. The data isn't time critical as long as it is within 15 minute window. 

any thoughts ? 


Michael

---

