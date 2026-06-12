---
title: "Karmic has killed video speed on Dell Mini 10"
date: 2009-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by critmcdonald on 2009-11-09
first ... i'm a Ubuntu Nube ... so bear with me.

I have a Dell Mini 10 that I installed the jaunty Ubuntu Netbook Remix (UNR) on. The video drivers were really bad and screen redraw was abysmal, so I searched around and found an answer to the problem: install Poulsbo graphic drivers: 
[http://credentiality2.blogspot.com/2009/08/accelerated-video-on-dell-mini-10-with.html](http://credentiality2.blogspot.com/2009/08/accelerated-video-on-dell-mini-10-with.html)

That worked great.

The I was prompted to update Ubuntu, which I did, so now I'm at Karmic? Well, the video went to crap again. I tried to install the Poulsbo graphic drivers again, but got lots of errors about missing packages and such.

Is there a way to fix this with Karmic? Or a UNR distro that is more friendly to my Dell Mini?

---

### Post by mikewhatever on 2009-11-09
The instructions to install the driver are pretty much the same, but as you noted, the same packages do not work. Try one of the scripts from this post--> [http://swiss.ubuntuforums.org/showpost.php?p=8182373&postcount=87](http://swiss.ubuntuforums.org/showpost.php?p=8182373&postcount=87)

---

### Post by critmcdonald on 2009-11-10
No luck with those 2007 scripts ... in fact I've completely hosed my Ubuntu install.

When I booted in recovery mode with networking it couldn't find host address "gma500re.altervista.org." Thinking maybe I was offline (remember newb comment from earlier ... I'd never booted in recovery mode) I booted as a normal user and was able to sudo wget at least something that brought the poulsbo_ppa.sh script into my home folder. It would not run as me, so I rebooted in recovery mode to be in root and tried again. Still no access. I chmod 777 and ran again, and it did run, but there were lots of errors, including the missing host address above. It did still remove a boatload of files, and indeed now when I reboot I no longer get the graphical Ubuntu login, but instead a command-line prompt to log into my machine.

So, I guess I go back to my 9.04 install on my thumb drive and then install the

---

