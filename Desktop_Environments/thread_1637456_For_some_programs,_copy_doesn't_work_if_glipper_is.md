---
title: "For some programs, copy doesn't work if glipper is running"
date: 2010-12-04
forum: Desktop Environments
---

### Post by leekyuh on 2010-12-04
Hi, 

I use glipper as a work-around for copy&paste bug for my Ubuntu 10.10.
However, in Kile, a popular tex editor, copying letters in the editor works only if glipper is NOT running.
If glipper is running, selected text is ignored and it pastes the last item in glipper's buffer  when I Ctrl+V.

Interestingly, however, if I right-click and select "Copy", it works. I verified that Ctrl+C is registered as copy shortcut in the settings. (Ctrl+C works if I close glipper.)
It seems that Ctrl+C is intercepted by glipper, but it fails to load the text into its buffer.
I can confirm that this problem is ubiquitous in all KDE applications, such as Konqueror and Kompare.

I have also  klipper(4:4.5.1-0ubuntu) installed on my system. I can't  remove it as it tries to remove kde-full and other core packages.
 
This happens even after updating Kile to the most recent version, 1:2.1.0~svn1112278beta4-2ubuntu1.
Any ideas?
This is very annoying problem for me and any kind of advice would be really appreciated..

Thanks!

Edit: This bug only happens in all kinds of text boxes in KDE apps, where you have blinking cursor for keyboard input.
(e.g. Address bar in Konqueror, text editor in Kile, etc.)

---

### Post by leekyuh on 2010-12-07
Bump. Nobody has this problem at all?
:-({|=

---

### Post by airplanesimen on 2010-12-07
can somone tell me what glipper is?
no, i dont have this problem, but i like to help:P
okey, i got glipper now... And i didnt got the same problem :/

---

### Post by leekyuh on 2010-12-07
Without glipper, you can't copy and paste text from one application, say firefox, into another, say gedit, if firefox is closed BEFORE pasting.
glipper keeps track of copied text in its own buffer, allowing users to copy & paste even if the source application is closed.
You can try and see by removing the "G" glipper icon on the applet bar, if you already have it.

More info: [https://help.ubuntu.com/community/glipper](https://help.ubuntu.com/community/glipper)

Edit: @airplanesimen, you need to add it to the task bar to enable it by pressing right-click on the empty task bar, Add to panel, Clipboard Manager.

---

### Post by airplanesimen on 2010-12-07
> **leekyuh said:**
> Without glipper, you can't copy and paste text from one application, say firefox, into another, say gedit, if firefox is closed BEFORE pasting.
glipper keeps track of copied text in its own buffer, allowing users to copy & paste even if the source application is closed.
You can try and see by removing the "G" glipper icon on the applet bar, if you already have it.

More info: [https://help.ubuntu.com/community/glipper](https://help.ubuntu.com/community/glipper)

Edit: @airplanesimen, you need to add it to the task bar to enable it by pressing right-click on the empty task bar, Add to panel, Clipboard Manager.

okey, now i understand... im using 10.10, and got no problems (very nice) try to reinstall it - then get the updates. what are u usinng? 10.10?

---

### Post by leekyuh on 2010-12-07
Yes, 10.10. Maybe glipper is installed as default?
If so, you can try copy&pasting text in Kile editor while glipper is running.
This bug happens on all kinds of text boxes only, where you can see blinking cursor for keyboard input.

---

### Post by airplanesimen on 2010-12-07
> **leekyuh said:**
> Yes, 10.10. Maybe glipper is installed as default?
If so, you can try copy&pasting text in Kile editor while glipper is running.
This bug happens on all kinds of text boxes only, where you can see blinking cursor for keyboard input.

yes, it works fine there too... so strange that your glipper isnt working properly..

---

### Post by leekyuh on 2010-12-07
Uh oh...
So you can actually copy & paste texts in Kile?
Which version of Kile do you have?

---

### Post by airplanesimen on 2010-12-07
> **leekyuh said:**
> Uh oh...
So you can actually copy & paste texts in Kile?
Which version of Kile do you have?

i got kile 1.2.1 beta4 i think. i saw some others got the same problem as you... Maybe its kile? or is it happening often in others programs too? If its only kile, i think u have to reinstall it. (i have tested it in a lot of text editors, programs and addons, but it works perfect for me:P) When im pasting, i can copy AND paste using the ctrl+(v or c) botton.

---

### Post by asmoore82 on 2010-12-07
I used to use glipper but always had it configured to ignore selected text in favor of ctrl+c and ctrl+v.

I now use parcellite instead. For me, it's been more stable and integrates into the notification area instead of its own applet.

P.S. If you install parcellite, you can find it under
"System -> Preferences -> Startup Apps"

---

### Post by leekyuh on 2010-12-08
@[asmoore82]("http://ubuntuforums.org/member.php?u=341737"): Thanks a lot! parcellite solved the problem. It's really simple but effective. Editing the buffer is also great feature.
It seems that glipper's Ctrl+C capture module has some problem on KDE applications.

---

