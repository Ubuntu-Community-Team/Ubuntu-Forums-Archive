---
title: "how to add google gadgets to start up ?"
date: 2009-02-19
forum: General Help
---

### Post by shateredsoul on 2009-02-19
Hi peoples,

So I found this guide [http://www.howtogeek.com/howto/ubuntu/how-to-add-a-program-to-the-ubuntu-startup-list-after-login/]("http://www.howtogeek.com/howto/ubuntu/how-to-add-a-program-to-the-ubuntu-startup-list-after-login/")that tells me how to add a program to the start up, the only problem is that I need to know where to find the program I want to launge.

I went to home/.google and could not fine a the executable file.. launch file.. deb file... whatever it's called, for google gadgets.  Can someone tell me how I can find this file? or another way to add google gadgets to start up?

If you know the terminal commands, can you also give the commands for taking it out of the start up programs list? Just in case I change my mind?

---

### Post by binbash on 2009-02-19
Go to System > Preferences > sessions and add

ggl-gtk -ns -bg

to command section

-bg means run at background -ns means semitransparent black sidebar won't appear

---

### Post by shateredsoul on 2009-02-21
ok so if I do want the semi-transparent bar to appear do I just leave that part off or put a plus sign in front?

anyone?

---

