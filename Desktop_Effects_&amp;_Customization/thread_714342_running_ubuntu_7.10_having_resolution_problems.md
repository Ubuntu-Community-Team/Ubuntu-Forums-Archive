---
title: "running ubuntu 7.10 having resolution problems"
date: 2008-03-03
forum: Desktop Effects &amp; Customization
---

### Post by KorovaOrange on 2008-03-03
I have a dell laptop with a Radeon RV250. I changed my resolution to 1280x1024 and after reboot i get a bunch of horizontal bands of color which are undoubtedly my start up screen. Problem is i cannot get to the proper screen to change my resolution back.

What I need is the proper commands in terminal that can get me to the standard res for my monitor.

The laptop is a Dell Latitude D600 if that helps at all.

I've just started using ubuntu a couple of days ago so don't be too harsh.

---

### Post by {BzF}~JOKesTER on 2008-03-05
Ok Do This:

When You get To The Screen {Where Your Supposed To Login}

Press:

ctrl+alt+f1

It Will Bring Up A Command Line

Now Press Enter {It Might Ask You To Login - If So Type Your Username And Password And Hit Enter}

Type: sudo dpkg-reconfigure -phigh xserver-xorg

And Then: sudo reboot

Your Computer Will Restart Now...

Now It Might Bring Up A Screen Saying Your Running In Low Graphics Mode - Thats Ok - 
Just Click Configure And Set The Resoulution And Graphics Drivers And Moniter Up Again.

Hope This Helps

---

