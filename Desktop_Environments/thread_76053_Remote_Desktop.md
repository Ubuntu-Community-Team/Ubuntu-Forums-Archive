---
title: "Remote Desktop"
date: 2005-10-14
forum: Desktop Environments
---

### Post by dwessell on 2005-10-14
Hi all.. After installing Ubuntu, I'm leaning towards making it the sole OS on the majority of my systems.. It was one of the nicest installs ever.. So kudo's to the deveopment team.

However, I have one issue that I haven't been able to figure out yet.. I have a PC that runs Windows XP Pro, and I use Remote Desktop to use the PC..  Heck, there isn't even a monitor hooked up to that PC..

Is there a program that will allow me to connect from an Ubuntu install, to that WinXP machine, and utilize it like Remote Desktop?

As well, if anyone knows of a good article on compiling programs from source, it would be appreciated.

Thanks
David

---

### Post by mbeach on 2005-10-14
I'm taking a guess in that this is what you want, but does the Terminal Server client do what you want?  
Applications | Internet | Terminal Server Client

---

### Post by mbeach on 2005-10-14
but better yet (IMO) installing UltraVNC or TightVNC Server on the WinXP might be a better option instead of the Microsoft Remote Desktop stuff.

ultravnc.sourceforge.net

---

### Post by Stormy Eyes on 2005-10-14
**mbeach** is right; the Terminal Services Client in GNOME should be what you need. It allows you to select between VNC, RDP, and RDPv5. The latter two are Remote Desktop Protocol, which is probably what you want.

---

### Post by dwessell on 2005-10-14
Thanks a ton.. I'm looking through the UltraVNC documentation now.. But I'm unclear on one thing.. Once I've installed this on the XP box, I'm using Terminal Server from the Linux box to connect to it? Would that be correct?

Thanks
David


[QUOTE=mbeach]but better yet (IMO) installing UltraVNC or TightVNC Server on the WinXP might be a better option instead of the Microsoft Remote Desktop stuff.

ultravnc.sourceforge.net[/QUOTE]

---

### Post by fheinsen on 2005-10-14
[quote=dwessell]Thanks a ton.. I'm looking through the UltraVNC documentation now.. But I'm unclear on one thing.. Once I've installed this on the XP box, I'm using Terminal Server from the Linux box to connect to it? Would that be correct?

Thanks
David[/quote]


You don't *have to* download UltraVNC or anything else in your Windows XP box.  Applications -> Internet -> Terminal Server Client allows you to connect to any Windows box that accepts remote connections -- no need for additional software needed anywhre.  

(The only reasons why you might want to install things like UltraVNC in Windows is to have additional security, better performance, or more functionality.)

---

### Post by dwessell on 2005-10-14
Wait NM, I think I see from UltraVNC... Thanks for all the input... :)

[QUOTE=dwessell]Thanks a ton.. I'm looking through the UltraVNC documentation now.. But I'm unclear on one thing.. Once I've installed this on the XP box, I'm using Terminal Server from the Linux box to connect to it? Would that be correct?

Thanks
David[/QUOTE]

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=dwessell]Thanks a ton.. I'm looking through the UltraVNC documentation now.. But I'm unclear on one thing.. Once I've installed this on the XP box, I'm using Terminal Server from the Linux box to connect to it? Would that be correct?[/QUOTE]

That's right. Whether you use RDP or VNC, you're using the Terminal Services Client on your Linux box to connect.

---

### Post by luna6 on 2005-10-14
I would recommend you use remote desktop / rdp to connect to the windows computer, it is a lot faster then vnc in performance, if you need to connect to other environments vnc is the way to go, but just to connect to a windows computer, rdp works best (it is optimized for windows by the microsoft beasts, so it feels like you are sitting at the desktop, vnc there is a noticeable lag when running).

---

### Post by dwessell on 2005-10-14
Hey all.. 

I've gotten to the point where I can see the other computer through the Network File Broswer, and can access it. But I haven't been able to use the Terminal Server Client yet.. It's asking for a Domain.. I've tried everysetting that I can think of her, localhost, workgroup, etc... (The computers are all on a Local Network).. What is the Domain asking for in this case?

Thanks
David


[QUOTE=luna6]I would recommend you use remote desktop / rdp to connect to the windows computer, it is a lot faster then vnc in performance, if you need to connect to other environments vnc is the way to go, but just to connect to a windows computer, rdp works best (it is optimized for windows by the microsoft beasts, so it feels like you are sitting at the desktop, vnc there is a noticeable lag when running).[/QUOTE]

---

