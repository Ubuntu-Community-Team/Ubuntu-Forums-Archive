---
title: "vmware and vista."
date: 2007-06-20
forum: Desktop Effects &amp; Customization
---

### Post by xl_cheese on 2007-06-20
Seems like everyone is running an XP virtual machine.  Is there a reason no one is using vista?

I have ubuntu installed on a partition on a 2nd HDD.  Can I use the Vista installation I currently have on my main HDD?

Or do I need a fresh install of windows?

thanks.

---

### Post by xl_cheese on 2007-06-20
Bingo.  

[IMG]http://i23.photobucket.com/albums/b369/xl_cheese/Screenshot.png[/IMG]

---

### Post by xl_cheese on 2007-06-20
BTW.  This is a fresh install on space created within the ubuntu partion by vmware server.

I played it safe and just went with vista ultimate after reading it was the only version of vista that will work.  Through employment I have access to all microsoft products via msdn.com subscription.

My original vista still resides on the other HDD on a dual boot.  for now...

If I can get this seamless I'll be a happy camper.

---

### Post by vco08 on 2007-06-20
i have Vista installed on my Vmware Workstation. Works good.

---

### Post by zero244 on 2007-06-21
VMware has a free program called Vmware Converter. Which makes an image of say your Vista install. Then you can import it into Vmware server and use it.
I believe you would run the Converter program within Vista to create the image.
Or you could do a fresh install of Vista into Vmware.
I would think since Vmware doesnt support 3D excelleration within a virtual machine Vista Aero might not work to well. But I havent tried it so I can only speculate. 
I run XP in a virtual machine and it works pretty well, its a touch laggy but useable.

---

### Post by dannymichel on 2007-06-24
I'm having a real hard time making my VMWare with Vista 32 bit Home Premium installed on my Ubuntu Feisty seamless as if it's a part of Ubuntu as I have seen on other guides and posts.

So far what I've done is:
[LIST]
[*]Install RDesktop
[*]Install Vista (Home Premium 32 bit) on VMWare
[*]InstallVMWare Tools on my Vista (Home Premium 32 bit) VM
[/LIST]

Some issues:
[LIST]
[*]One issue is that I can't connect to the internet on my VM when I use a "Host Only" connection.
[*]No sound card installed on VM
[/LIST]

---

### Post by dannymichel on 2007-06-25
If I'm missing something and there is a thraed that solves my issue I would appreciate it if someone would direct me to that thread and post.

---

### Post by xl_cheese on 2007-06-25
vista home will not work.  Only vista ultimate or business.

These things are also mentioned in the big how-to seamless thread.

---

### Post by rjs82vette on 2007-07-17
No matter how many times you post the same question the answer is that Home does not support remote desktop so seamless windows/ubuntu will not work.

---

