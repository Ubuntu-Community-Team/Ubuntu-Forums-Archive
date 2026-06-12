---
title: "Ubuntu not installing on Inspiron 500m"
date: 2012-03-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jbruckner on 2012-03-24
Hello Everyone,

I am very new to Ubuntu and I am trying to set up my school that I work at with student laptops. I received a ton of laptop computers donateted to the school, but they do not have operating systems and the IT person and I decided to install Ubuntu because of it being free and very easy to use. Things were going great until I got to the Dell Inspiron 500m's that were detonated. Windows loaded without an issue so I know the hard drives are good, but when I try to load and install Ubuntu it starts reading the disk and then all of a sudden the screen goes black and the computer seems to lock up. 

Any help would be great. I want to get these computers to the students in the school so that they have another way of using technology that they have not had before. 

Thanks in advance,

Jeremy

---

### Post by wojox on 2012-03-24
Do you know which graphics card they have? Assorted? Try F6 and "nomodeset".

---

### Post by jbruckner on 2012-03-24
Is this something I have to do while in the Ubuntu operating system? 

From the set up menu is shows the video controller is an Intel 855GM

Sorry I have VERY basic understanding of these types of things.

---

### Post by gbrainin on 2012-03-24
I found a similar-sounding problem, and its solution, here: [http://pragmatec.blogspot.com/2010/05/ubuntu-1004-lucid-lynx-on-dell-inspiron.html](http://pragmatec.blogspot.com/2010/05/ubuntu-1004-lucid-lynx-on-dell-inspiron.html)

---

### Post by jbruckner on 2012-03-25
Still no luck. I followed the directions in the link provided and still nothing. How do I wipe the hard drive to start over fresh?

---

### Post by gbrainin on 2012-03-25
Generally, when you install the operating system it formats the hard drive as part of that process; it's not something you usually have to do as a separate step.

As for your computers, most likely there's some piece of hardware in there that requires a workaround rather than the ordinary installation process.  Search for the particular version of Ubuntu you're using, along with the computer model or graphics card model (most likely culprits), and hopefully you'll find someone who had the same problem and solved it.

---

### Post by ugm6hr on 2012-03-27
I used to own one of these... The problem is the graphics display.
You need to use the vesa driver at startup. I can't remember if these options are still available with the LiveCD on Ubuntu.

Have a read of this - and see if it seems to be the same problem you have:
[http://askubuntu.com/questions/95287/ubuntu-crashes-when-trying-to-boot-install-disk](http://askubuntu.com/questions/95287/ubuntu-crashes-when-trying-to-boot-install-disk)

---

