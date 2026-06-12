---
title: "Execute program on virtual machine"
date: 2009-06-07
forum: General Help
---

### Post by WitchCraft on 2009-06-07
Hi, question:

I have a program installed on a VirtualBox running Ubuntu x64 on Windows Vista.

What I want to know is how I can execute a program on the Virtual Ubuntu from my Windows installation.

I'd assume either via ssh or via an VirtualBox API, and exchange data via a windows share?

Is that correct?

(I need to call a program that runs on Linux from Windows, and get the result (may be files) back to windows).

I'd assume anohter way would be to write a client/server program and let the server run under Linux, and access it via client from Windows and transmit the data via tcp... (which would basically be a substitute for ssh)

---

### Post by blueridgedog on 2009-06-07
You would install the ssh server on the virtual machine, and then get an ssh client for windows (like putty) and you could ssh using the internal ip addressing scheme.

For moving files, there is sftp that will work over ssh (only one thing to setup).  Cygwin may give you that on the windows site:

[http://www.cygwin.com/](http://www.cygwin.com/)

If that is not what you want, you can setup a samba share on the ubuntu system.

---

### Post by WitchCraft on 2009-06-07
> **blueridgedog said:**
> 

If that is not what you want, you can setup a samba share on the ubuntu system.

I thought it would be easier to setup a windows share on the vista machine and access the windows share from ubuntu. that way I wouldn't have to install a samba server on the virtual box.


But now that I think about it, I think it's probably safer to set up the share on the virtual machine.
I'm not sure though, and it might be slower than vice-versa.

Anybody can confirm/deny that assumption?

Anyway, will a sama share be persistent? (on restart?)

---

### Post by blueridgedog on 2009-06-07
> **WitchCraft said:**
> 
I'm not sure though, and it might be slower than vice-versa.

Anybody can confirm/deny that assumption?

Anyway, will a sama share be persistent? (on restart?)

Well, you can try it each way and see what you think.  It should be persistent.

---

