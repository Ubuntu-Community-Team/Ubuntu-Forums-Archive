---
title: "Fluxbox ontop Xubuntu: Do undesireable Xfce components still load?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by snakyjake on 2006-09-26
I installed Fluxbox ontop of Xubuntu.  
Do undesireable Xfce components still load, or do I get a "pure" Fluxbox?

If someone could also explain further what happens when window managers are installed ontop of each other.  For example, if someone installs Xfce from Ubuntu, are they getting all the lightweight advantages of Xfce, or do some components of Ubuntu/GNOME still load?  The same goes for installing Fluxbox ontop ov Xubuntu.  I'm concerned that components of Xubuntu are still loaded since I still see the Xubuntu startup.

Startup appearance and load time is the same up to the session login.  After logging in, Fluxbox is quicker.  I don't see any processes from running TOP that have xfce in the name, so I assume I have a pure fluxbox window manager.

Thank you,

Jake

---

### Post by catlett on 2006-09-26
If you want a straight fluxbox ubuntu, there is nubuntu. It is not maintained by canonical like kubuntu,xubuntu and ubuntu. It is a seperate project by 'network' enthusiasts. Anyways here is the link [http://www.nubuntu.org/about.php](http://www.nubuntu.org/about.php)
I personaly run ubuhtu-lite, it uses icewm as the window manager, I haven't tries installing nubuntu yet. [http://www.ubuntulite.org/drupal/?q=node/1](http://www.ubuntulite.org/drupal/?q=node/1)

---

### Post by snakyjake on 2006-09-26
What is meant by "straight fluxbox"?
> If you want a straight fluxbox ubuntu, there is nubuntu.

I hear this word quite a bit when referring to installing different window managers.  It makes it sound like if I had previously installed (K|U)buntu, and then installed Xubuntu or Fluxbox, then I'd still have some components of KDE/GNOME loading as well.  I need more clarification.

Another way of asking the question: What is the difference between installing a window manager via apt versus "straight"?

The ultimate goal is to have a window manager only loading and consuming the resources that belong to itself.  If I run Fluxbox, I don't want components of Xfce, or Gnome, or KDE to be running. I'm only concerned with the CPU and RAM resources, and not that I have used up more hard disk space by installing multiple window managers.

Thanks,

Jake

---

### Post by catlett on 2006-09-26
> **snakyjake said:**
> What is meant by "straight fluxbox"?


I hear this word quite a bit when referring to installing different window managers.  It makes it sound like if I had previously installed (K|U)buntu, and then installed Xubuntu or Fluxbox, then I'd still have some components of KDE/GNOME loading as well.  I need more clarification.

Another way of asking the question: What is the difference between installing a window manager via apt versus "straight"?

The ultimate goal is to have a window manager only loading and consuming the resources that belong to itself.  If I run Fluxbox, I don't want components of Xfce, or Gnome, or KDE to be running. I'm only concerned with the CPU and RAM resources, and not that I have used up more hard disk space by installing multiple window managers.

Thanks,

Jake


Sorry for the delay. I said 'straight' because fluxbox on nubuntu will be the only window manager. 
With nubuntu those guys did a server install. Then they only added the apps they wanted. With ubuntu/kubuntu you are getting a 'meta-package' with lots of libraries and applications. The nubuntu guys wanted to keep it simple and only have the tools they wanted.
I am not sure about what resources run when you have multiple managers. I do know I can run kde applications from gnome. Does that mean gnome is using the libraries or does it mean kde services are running?
I want to say there is only one window manager and session manager running and the only thing affected is disk space because you added libraries but I don't know for sure.
You might have to do a little research. Add the System monitor to your panel. (right click on the top panel and  It will show your running processes. Right now I am only showing gnome applications, no processes associated with a different manager.

---

### Post by kerry_s on 2006-09-26
Your setup is fine just consider the xfce4 as extra applications. You choose whether you want to use them in fluxbox or not. The xfce4 stuff does not get loaded with fluxbox.

A straight install of fluxbox, is when you only have fluxbox and no other DE(desk environment) or WM(window manager). You can get a straight install by using the alternate cd and doing a server install, then apt-getting the desktop you want.

---

### Post by snakyjake on 2006-09-26
Thanks for the answers.  I have to say, I'm really impressed with the Linux modularization.  I was worried that installing Fluxbox ontop of another would diminish the advantages (except for hard disk space), and glad it isn't true.  I really like the idea of being able to trial different environments without having to reinstall, or lose data.  I like the idea I can have more than one environment. And since the risk of trying something new is near zero, the chance of finding something that better suits my needs is very high.  So far Fluxbox is exactly what I expected...it's fantastic.  

Linux keeps opening up doors for me \\:D/

Thanks!

---

