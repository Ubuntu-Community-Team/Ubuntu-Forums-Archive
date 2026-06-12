---
title: "gksudo failure"
date: 2006-07-01
forum: Desktop Environments
---

### Post by catlett on 2006-07-01
All of a sudden I can't run as a different user.  I never had a problem with gksudo. I have a root nautilus and root terminal that launch fine by the launcher or terminal, As well as any gui that I use gksudo with.
Anyways I just tried to launch synaptic with gksudo and I got this error
> tj@ubuntu:~$ gksudo synaptic
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key

(synaptic:8010): Gtk-WARNING **: cannot open display:
tj@ubuntu:~$

I just tried my root terminal and my root nautlius they fail as well. When I tried to launch them, the "run as a different user" prompt comes up asking for my password. I enter it, the prompt goes away but nothing launches.

Anyone ever had an issue like this? What is invalid MIT-MAGIC-COOKIE? I eat chocolate chip:p 

Seriously, does anyone have an idea? Also nautilus and the terminal launch without an issue when I launch them as user.

Thanks.

---

### Post by catlett on 2006-07-01
I have narrowed it down but I am now stuck. Basically I lost gksudo/run-as-a-different-user ability.
The error MIT etc. occurs when you try to open a window as a different user but you don't have the authority to do it. (or so a mail thread I found says)
So this is where I am stuck. What is gksudo. Is it an application? Is it a file in x somewhere. For the heck of it I ran apt-get gksudo and got  "No candidate version found for gksudo"
How can I modify or create gksudo?

P.S. I can use su to get a root terminal and then run synaptic no problem. It's just an error when running as a different user.

---

### Post by aysiu on 2006-07-01
You can try these two fixes--see which one works:
[http://lists.suse.com/archive/suse-linux-e/2001-Feb/0069.html](http://lists.suse.com/archive/suse-linux-e/2001-Feb/0069.html)
[http://www.linuxforums.org/forum/linux-desktop-x-windows/59110-x-login-error.html](http://www.linuxforums.org/forum/linux-desktop-x-windows/59110-x-login-error.html)

---

### Post by catlett on 2006-07-02
[QUOTE=aysiu]You can try these two fixes--see which one works:
[http://lists.suse.com/archive/suse-linux-e/2001-Feb/0069.html](http://lists.suse.com/archive/suse-linux-e/2001-Feb/0069.html)
[http://www.linuxforums.org/forum/linux-desktop-x-windows/59110-x-login-error.html](http://www.linuxforums.org/forum/linux-desktop-x-windows/59110-x-login-error.html)[/QUOTE]
Just wanted to say thank you for taking the time to find me a couple of links and posting. The second post was exactly what is happening to me but I couldn't find the files the poster modified.
In the end I just reinstalled. I have been wanting an excuse to reinstall because this will be the first time I reinstalled with a home partition. 
Ubuntu is easy to install and setup as it is but with a home partition it is even easier. Because my desktop, themes etc were untouched all I had to do was change my sources list and install codecs and plugins. The entire procedure from booting to the install to back to where I was before the error was 45 minutes. 
I think this is going to be my new way to troubleshoot, I won't troubleshoot. Reinstalling is faster. I spent 3 hours googling and trying stuff to no avail. I finally did a 45 minute reinstall and everything is fixed. Next time I'm goingh straight to reinstall. :p 

Anyways I just wanted to say thank you.
Regards,

Catlett

---

### Post by kinematic on 2006-07-02
[QUOTE=catlett]Next time I'm goingh straight to reinstall. :p [/QUOTE]

that's how you learn things....just reinstall ;)

---

### Post by beom on 2006-07-09
Yep.
To reinstall EVERYTHING, at least at my system, wouldn't take 45min.
:D

---

