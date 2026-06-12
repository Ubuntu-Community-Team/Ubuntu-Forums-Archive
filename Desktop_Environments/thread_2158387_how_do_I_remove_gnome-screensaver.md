---
title: "how do I remove gnome-screensaver?"
date: 2013-06-28
forum: Desktop Environments
---

### Post by cybergalvez on 2013-06-28
I updated from 12.04 to 13.04 going through 12.10. I like gnome-shell but after the update gnome-shell was not working properly, it looked the the composting was not working, and it didn't start working until I install the "gnome" package. Now I want to use xscreensaver, so I have to remove gnome-screensaver, which If I try to the system wants to remove gnome and gnome-core, which messes with the composting and no gnome-shell after that.

So how can I remove gnome-screen saver so that I can use xscreensaver?

Thanks in advance for the help

---

### Post by cybergalvez on 2013-06-28
taking a different apporach, I am trying to run gnome-screensaver-command --exit to turn the it off but I can't seem to figure out how to get my script to run at the right time to it. I've added it to the startup items but gnome-screensaver is still running after I login.

---

### Post by hansdown on 2013-06-28
Hi  cybergalvez.

Hope this helps.

[http://www.ubuntututorials.com/add-screensaver-ubuntu-12-04/](http://www.ubuntututorials.com/add-screensaver-ubuntu-12-04/)

---

### Post by cybergalvez on 2013-06-28
Thanks unfortunately if I try to remove gnome-screensaver apt whats to remove gnome then gnome-shell stops working

---

### Post by cybergalvez on 2013-06-29
ok figured it out. I created a script to run gnome-screensaver-command --exit followed by xscreensaver -no-splash, but that wasn't working. As far as I can tell it must have been either a race condition or the gnome-screensaver daemon was started after my script was run but the bottom line it wasn't working. So I added a delay, now when I launch my script it waits 3 minutes before trying to kill gnome-screensaver and launching xscreensaver. Now its working just fine, the only issue since I'm not really good with bash scripts I have a python script that manages the delay that then runs a bash script to shutdown gnome-screensaver and launch xsreensaver. I first tried doing it all in python but that didn't work either so hence the two scripts.

---

### Post by JonHale on 2013-12-15
Since I too also wanted to run gnome-shell, I didn't want to remove the gnome-screensaver package (which would also remove the gnome-core package). <br>
<br>
And since I couldn't see a way to NOT start gnome-screensaver. I created the following shellscript (XScreenSaverStart - because what I really want to do is start the xscreensaver without having it fight with the gnome screensaver):<div style="margin-left:40px"><br>
</div>```
#!/bin/sh<br>
while sleep 1<br>
&nbsp;&nbsp; &nbsp;do<br>
&nbsp;&nbsp; &nbsp;if gnome-screensaver-command --query 2&gt;&amp;1 |<br>
&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;grep --silent "Screensaver is not running"<br>
&nbsp;&nbsp; &nbsp;then<br>
&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;/bin/true<br>
&nbsp;&nbsp; &nbsp;else<br>
&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;gnome-screensaver-command --exit<br>
&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;sleep 1<br>
&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;xscreensaver -no-splash &amp;<br>
&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;exit<br>
&nbsp;&nbsp; &nbsp;fi<br>
done<br>
<br>

```<br>
<br>
Then I run the "Startup Applications" program to add this as a startup application.<br>
After logging out and logging back in, all was set.<br>
<br>
<br>

---

### Post by JonHale on 2013-12-15
Sorry, I am not sure how I managed to get the html formatting characters in my last post.
Here is the code (hopefully without the annoying html):
```
#!/bin/sh
while sleep 1
do
    if gnome-screensaver-command --query 2>&1 |
        grep --silent "Screensaver is not running"
    then
        /bin/true
    else
        gnome-screensaver-command --exit
        sleep 1
        xscreensaver -no-splash &
        exit
    fi
done



```

---

