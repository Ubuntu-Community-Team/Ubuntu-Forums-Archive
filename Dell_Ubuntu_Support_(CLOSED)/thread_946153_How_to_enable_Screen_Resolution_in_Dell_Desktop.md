---
title: "How to enable Screen Resolution in Dell Desktop"
date: 2008-10-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sukhhari on 2008-10-13
How to Enable Screen Resolution 1024*800 or something else in Dell Desktop
(Optiplex 740)

Regards

Harish:confused:

---

### Post by andybleaden on 2008-10-13
> **sukhhari said:**
> How to Enable Screen Resolution 1024*800 or something else in Dell Desktop
(Optiplex 740)

Regards

Harish:confused:

Well although I use kubuntu .... I am sure that you will will be able to manage it similarly. I went into my system settings>monitors>hardware (log in as admin)>select my monitor from a list using the button 'find my model' and it did it automatically for me. It may not be the exact same route but let me know how you get on

Hope that helps

---

### Post by andybleaden on 2008-10-13
I also forgot to add that after selecting your model ...you can then set the most appropriate screen settings...although if your model is listed it will select the default

---

### Post by sukhhari on 2008-10-13
All that activity done, my actual problem is that, after enabling the Nvida drivers System get Crashing.

:popcorn:

---

### Post by johnmata on 2008-10-13
> **sukhhari said:**
> All that activity done, my actual problem is that, after enabling the Nvida drivers System get Crashing.

:popcorn:

Hello,  you may be using the wrong driver for your video card.  Let EnvyNG take the guess work out of the equation for you.  Go to this [link]("http://johnmata.com/index.php?blogid=1&archive=2008-10-12").  This article is on how to set up dual monitors, but once you have the NVIDIA Server settings application running you can use it for your resolution settings instead.  Be sure that you open NVIDIA Server settings application with sudo, otherwise you won't be able to save to your xorg.conf file! And be sure that you actually have NVIDIA, as you may have an ATI.  I believe your computer can come with either.

Hope this helps,
John

---

