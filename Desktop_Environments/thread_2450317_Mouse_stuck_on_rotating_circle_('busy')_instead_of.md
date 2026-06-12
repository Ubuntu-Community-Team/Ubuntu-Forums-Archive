---
title: "Mouse stuck on rotating circle ('busy') instead of arrow"
date: 2020-09-11
forum: Desktop Environments
---

### Post by John Jason Jordan on 2020-09-11
I have long used cheap Logitech mice on my computers, including my laptop, all running Xubuntu 18.04. On the laptop the touchpad is disabled, so the mouse is the sole pointing device. Suddenly, in the process of installing and uninstalling small applications, the mouse cursor got stuck on the rotating circle instead of the pointer. Normally the rotating circle only happens briefly while an application is busy, but now it is on constantly on the desktop.

I have tried without success:
	Unplugging the mouse's USB receiver and then back in again
	Removing the battery from the mouse, and putting it back in
	Various epithets and expletives

I also looked at the GUI task manager, hoping to find some process to kill. Total CPU usage seems to be about 4%, and disk usage is also negligible. I am guessing that I closed an application, causing the circular icon to appear, and the application terminated without turning off the 'busy' icon. Unfortunately, in task manager there are several dozen processes with indecipherable names, so I have no way to tell what to kill.

I am sure that if I rebooted or just logged out and back in again the problem would resolve itself, but I shouldn't have to take such measures just to fix this little problem. Does anyone know what process makes the 'busy' icon appear? Or any other way to make the normal mouse icon go back to the pointer?

---

### Post by Autodave on 2020-09-11
Logging out and back in again doesn't sound like such a big deal.  That would be the very first thing that I would have done.

---

### Post by John Jason Jordan on 2020-09-11
> **Autodave said:**
> Logging out and back in again doesn't sound like such a big deal.  That would be the very first thing that I would have done.

Thanks for the thought, but rebooting is about the same effort. Logging out shuts down all apps that are open on the desktop. At this time I have open a mail client, two browsers, each with a couple dozen tabs, two torrent clients, my VPN, six PDF files, three LibreOffice files, and a dozen more small utilities. Restoring all that would take close to half an hour, and that's assuming nothing goes wrong in the process. And something usually does go wrong. 

More to the point, I'd really like to know what process makes the mouse pointer change from the normal pointer to the 'busy' rotating circle. The mouse doesn't just do that all by itself; there must be something that triggers it.

---

### Post by John Jason Jordan on 2020-09-12
I discovered a web page listing CSS values for the various states of the cursor:

	[https://infoheap.com/css-cursor-property/]("https://infoheap.com/css-cursor-property/")

And apparently the value for what I call the 'busy' rotating circle is Wait, while the normal value is supposed to be set to Auto. Unfortunately the page did not elucidate where these settings reside on a Linux computer. Wherever they are, my guess is that something overrode my Auto setting with Wait, so all I should have to do is change it back to Auto.

I've poked around in all the settings I can find on my Xubuntu computer, but so far I haven't found the secret hiding place for them. Any ideas?

---

