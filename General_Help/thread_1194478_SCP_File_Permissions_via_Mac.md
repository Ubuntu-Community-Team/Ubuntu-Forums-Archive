---
title: "SCP File Permissions via Mac"
date: 2009-06-22
forum: General Help
---

### Post by fozzyuw on 2009-06-22
Here's a problem.

I have OpenSSH running on my Ubuntu Server.  I've locked it down using the built in chroot option.

I use WinSCP to transfer files from my Windows computer.  Doing so, gives RW-R--R-- permissions to the file.

Using a Mac and Fugu, the file permissions default to RWX------.

Any idea how to get the Mac to use RW-R--R-- permissions as well?  I would guess it has something to do with Mac's OS X being built around Unix and uses the same/similar permission rules so it's just copying over permissions from the local computer to the server.

What I want to do is allow our graphic designer to not have to remember (because she won't) to change the file permissions every time she uploads something.

Ideas?

Cheers!
Fozzy

---

