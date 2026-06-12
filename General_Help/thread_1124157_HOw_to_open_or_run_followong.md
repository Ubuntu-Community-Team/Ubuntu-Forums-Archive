---
title: "HOw to open or run followong"
date: 2009-04-13
forum: General Help
---

### Post by tony12 on 2009-04-13
Hi Everyone!

I woulkd like to open or run 'NVIDIA-Linux-x86_64-180.44-pkg2.run'. What packages do I need to install to do so?

Thank you

---

### Post by zvacet on 2009-04-13
Right click on package and tick make file executable (or something like that) and then close package and double click on it.[Here]("https://help.ubuntu.com/8.04/add-applications/C/install-file.html") is exact instruction.

---

### Post by tony12 on 2009-04-13
Hi! Thank you for that. I have done that and then it come up with'  ERROR: nvidia-installer must be run as root'

what now?

Thank you

---

### Post by Michael.Godawski on 2009-04-13
hey tony12, 
try 
```
sudo sh NVIDIA-Linux-x86_64-180.44-pkg2.run
```while being in the correct directory.

So open the terminal and navigate with cd to the directory where the file is located, for instance
```
cd Desktop
```

---

### Post by overdrank on 2009-04-13
And to add to Michael.Godawski you will need to exit X

You may use this command if you are using gnome ```
sudo /etc/init.d/gdm stop
```

---

### Post by tony12 on 2009-04-13
Hi!

Thanks . I have done that and now it come up with 'ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).'

I went to read me file but it I just got lost.

Please help. I am new to ubuntu so even the simple thimgs to most  might not be for me, for now anyway.

Tha nk you

---

### Post by 3rdalbum on 2009-04-13
> **tony12 said:**
> Hi!

Thanks . I have done that and now it come up with 'ERROR: You appear to be running an X server; please exit X before            
         installing.

Use the command that Overdrank gave you:

```
sudo /etc/init.d/gdm stop
```

This stops the X server and leaves you at a terminal prompt. Run the installer. Afterwards you will need to run this command:

```
sudo /etc/init.d/gdm start
```

to get back to the graphical session.

Also, it wasn't mentioned before, but **you will need to install the headers for your kernel** - install the package "linux-headers" in Synaptic Package Manager *before* running the gdm stop command.

As was said in your other thread, usually you'd be able to install the Nvidia driver through the Hardware Drivers program. This is the last resort method. And no, I have no idea why Nvidia's installer needs you to disable your graphics server in order to install; no other driver requires this of you.

---

### Post by overdrank on 2009-04-13
> **3rdalbum said:**
> As was said in your other thread, usually you'd be able to install the Nvidia driver through the Hardware Drivers program. This is the last resort method. And no, I have no idea why Nvidia's installer needs you to disable your graphics server in order to install; no other driver requires this of you.

I would have to agree with 3rdalbum. If you install the nvidia drivers like you are attempting you will need to reinstall after every kernel update.
In your other thread you have a sis graphics.
 Did you get a new card and if so what is the model?

---

### Post by tony12 on 2009-04-13
Hi!

I'm new to ubuntu. Have been playing with it last 4 weeks. My graphics card is GigaByte 76ooGT

---

### Post by overdrank on 2009-04-13
> **tony12 said:**
> Hi!

I'm new to ubuntu. Have been playing with it last 4 weeks. My graphics card is GigaByte 76ooGT

Have you tried the restricted drivers located under system, administration, hardware drivers?

---

### Post by tony12 on 2009-04-15
Hi!

Just wanted to say thank you all I have sort it out.

---

