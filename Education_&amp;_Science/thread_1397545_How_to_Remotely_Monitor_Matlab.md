---
title: "How to Remotely Monitor Matlab?"
date: 2010-02-03
forum: Education &amp; Science
---

### Post by Klaw198 on 2010-02-03
Hi, I currently work at a lab which uses Matlab to do calculations that take weeks.  We're having problems monitoring Matlab outside of the lab.  Specifically, what we would like would be to have Matlab run on a linux computer in the lab and be able to check up on it every so often.  We've tried playing around with X server and are going to try VNC when there's time.  If anybody has a solution to this it would help out a lot!  Thanks.

---

### Post by sudomp on 2010-02-04
Matlab can be run in the background persistently (continues even after you logout) using nohup.

$ nohup matlab -nodisplay -nodesktop -nojvm -nosplash -r script.m > output &

& view the output live with
$ tail -f output

[http://www.mathworks.com/support/solutions/en/data/1-15F5B/index.html](http://www.mathworks.com/support/solutions/en/data/1-15F5B/index.html)

---

### Post by ahmatti on 2010-02-05
I'd suggest using GNU screen: [http://www.gnu.org/software/screen/](http://www.gnu.org/software/screen/)

```

screen
matlab -nodisplay -nodesktop -nojvm -nosplash
#Close your connection, e.g. close the shell, logout
#Log back into the server
screen -r 

```

Also see a quick screen tutorial:
[http://news.softpedia.com/news/GNU-Screen-Tutorial-44274.shtml](http://news.softpedia.com/news/GNU-Screen-Tutorial-44274.shtml)

If you can use VNC, that of course works too. The good part about screen is that you can use it without X-server.

---

