---
title: "Software Center (still crashing) followed previous entry"
date: 2013-09-29
forum: Desktop Environments
---

### Post by rasch53144 on 2013-09-29
All:

While I am a noob, to the forumns, I try to live by the motto read first and ask questions later.  I have followed the previous advice and removed software center and added it back.  I have been trying to understand what PID 3269 Core 5 error is.  Yes, I have a Dell Inspiron 3520.  Here is the log file after the restore. Intel® Core™ i5-3210M CPU @ 2.50GHz × 4 
Intel® Ivybridge Mobile , 6 GM RAM


ERROR: apport (pid 3397) Sun Sep 29 12:12:33 2013: called for pid 3269, signal 5, core limit 0
ERROR: apport (pid 3397) Sun Sep 29 12:12:33 2013: script: /usr/share/software-center/software-center, interpreted by /usr/bin/python2.7 (command line "/usr/bin/python /usr/bin/software-center")
ERROR: apport (pid 3397) Sun Sep 29 12:12:34 2013: debug: session gdbus call: (true,)

Any direction would be appreciated.  I have managed and learned quite about from not using software center, yet would enjoy having the interface back again.

Thanks

---

### Post by ibjsb4 on 2013-10-01
Software-center crashing seems to be going around.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+center+crashing&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+center+crashing&sa=Search&cof=FORID:9)

I would suggest just using another package manager until you get it figured out.

[synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9")

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get install synaptic
```

---

### Post by rasch53144 on 2013-10-01
Thank you!  I agree the other packages are working great.

---

