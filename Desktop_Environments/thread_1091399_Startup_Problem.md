---
title: "Startup Problem"
date: 2009-03-09
forum: Desktop Environments
---

### Post by handyman on 2009-03-09
I have just installed Ubuntu 8.10, dual booting with win XP. All went well and I transferred my data files from my Kubuntu 8.04 computer, everything was fine. I shut down last night as normal and when I booted up today I get a normal bootup sequence until I reach a plain gold screen then everything stops and the screen remains blank. If I press ctrl-alt-F1 I get a cmd line login but I dont know how to go about fixing this problem. Can anyone tell me how to proceed from here?

---

### Post by acid_burns on 2009-03-10
I have the same problem i upgraded from 8.04 and restarted and it put me in termininal login mode i loged in and tryed start up X using the startx command but said failed to connect to server error, but it is not the server i down loaded it is the desktop version.The 8.04 works great should i just stick with this version or is there advantages to upgrading to 8.10?

Thanks

---

### Post by gexas on 2009-03-10
Hi..
I have this problem too.. but i try to change session to terminal and finded out so gnome package not installed.. so i installing it now...
And tell you guys later, if it help me, or no.. ;)

---

### Post by gexas on 2009-03-10
> **gexas said:**
> Hi..
I have this problem too.. but i try to change session to terminal and finded out so gnome package not installed.. so i installing it now...
And tell you guys later, if it help me, or no.. ;)

Ok.. 
I tryied this..
It's begin load and halt on black screen but mouse still alive.. 
So i think, reason is my integrated video card with 8mb. memory.. 
I tryed before install the xubuntu on my computer and it runs normaly.. so you can try install the xubuntu desktop enviroment, from the terminal session.

Finaly i make it run..
i selected sesion : failsafe terminal and run this command:

sudo apt-get install xorg fluxbox

For this you need a active internet connection..
After it, i type:

exit

and select session fluxbox, then log into...

---

### Post by handyman on 2009-03-10
Problem Resolved

I found the answer to my problem in post #1059426 "unnstalling Evolution messed up my startup" I had done the same thing earlier in the day and all seemed fine. It was not till I booted up the next day that the problem occurred and I did not connect it to the uninstall of Evolution. The fix was to run "sudo apt-get install evolution" then "sudo apt-get install ubuntu Desktop"

---

### Post by gexas on 2009-03-12
> **handyman said:**
> Problem Resolved

I found the answer to my problem in post #1059426 "unnstalling Evolution messed up my startup" I had done the same thing earlier in the day and all seemed fine. It was not till I booted up the next day that the problem occurred and I did not connect it to the uninstall of Evolution. The fix was to run "sudo apt-get install evolution" then "sudo apt-get install ubuntu Desktop"

This is nice man.. =D> thanx..

---

