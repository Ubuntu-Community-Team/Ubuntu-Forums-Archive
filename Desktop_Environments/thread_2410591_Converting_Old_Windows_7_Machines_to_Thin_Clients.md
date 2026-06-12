---
title: "Converting Old Windows 7 Machines to Thin Clients"
date: 2019-01-17
forum: Desktop Environments
---

### Post by SpenceMakesSense on 2019-01-17
Hey Ubuntu Forums! Long time, no post.

So I have an idea for the environment I currently work in. Pretty much everyone logs into their Windows PC, then remotes into a Windows Server. Since Windows 7 is dying in about a year, and I've grown to really dislike Windows, AND I want the company to save a bit of money, I figured converting them to thin clients via Linux would work pretty well. 

I seeked out the lightest weight version of Ubuntu, which is Lubuntu from what I can tell. I wanted a gui based version of Linux to make life easier for me, and to have as an emergency backup workstation for the user if something went wrong. 
Basically I want the final product to do the following:
Auto Login to Lubuntu using a basic user account
Auto connect to the Windows Terminal Server
Prompt for login via Windows and not Lubuntu

I've been connecting to our server via Remmina. Not married to the program, but it works well. I've gotten the computer to login as basic user and auto connect to the server, but I've run into a couple snags.

When I first setup Remmina, I could set the Security type to "RDP" and it would connect, then prompt for a login via Windows. After a reboot, that has stopped working . Just gives the error " Unable to establish a connection to RDP server 'server'". I know you're gonna ask for a log file, but after a little googling I honestly couldn't find a definitive source on where it is.

So the alternative is to just have it ask for the password *before* connecting to the server using NLA. My issue here is that it gives an option to save password and auto logs in as that user from then on if you check that box.I really don't want that option since people tend to jump around to different workstations. I can tell the users to not check that box, but I'm sure they will anyways. 

I tried to make it so the file was "read-only" (made owner the admin account, made admin account the only one allowed to change it) but it seems like as soon as you start Remmina it changes those permissions. Bit stumped on this one and it's been a tough one to Google for sure. 

I'm open to other RDP client alternatives too, Remmina just seemed pretty smooth up until now. 

Let me know what you guys and gals think.

---

### Post by jglen4902 on 2019-01-25
I know nothing about Remmina, except what is at their web page.  Did you use the install entries found there?
[https://remmina.gitlab.io/remminadoc.gitlab.io/](https://remmina.gitlab.io/remminadoc.gitlab.io/)

Apparently there is a snap, a flatpak, and a ppa - your choice!

---

