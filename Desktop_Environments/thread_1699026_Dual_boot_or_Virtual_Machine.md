---
title: "Dual boot or Virtual Machine?"
date: 2011-03-03
forum: Desktop Environments
---

### Post by garfonzo on 2011-03-03
Hey Folks:

I'm about to switch over to Ubuntu as my main OS but still need a few programs in Windows. Occasionally, and I mean like once every two to three months, I need to boot up either Photoshop or Microsoft Access and do a bit of work. Originally I was thinking that when I switch to Ubuntu, I can just set up a dual boot situation for using the Windows apps. However, why use 10GB or so of hard drive space when I will only use it every few months? (My hard drive is only 80GB as all my documents are stored on a server)

So, my thought is, what about setting up a Virtual machine to run my programs? Would this work? I could install my copy of Windows, Adobe and Office on this virtual machine to use on the random occasions I need them. What do you think?

Thanks,

---

### Post by YesWeCan on 2011-03-03
You'll need 10GB+ whatever you do. That's what Windows consumes.
Oracle VirtualBox is a very convenient way to achieve what you want and allows you to run Windows and Ubuntu concurrently, which is handy.
You need 3GB+ RAM for comfort.

---

### Post by nomko on 2011-03-03
If it's only once in 2 or 3 months that you need Photoshop (and Windows), then a VM is much better. 
Main reasons: No hard disc space is used by an operating system which is used once in a few months, you don't get in any trouble with Grub, you won't get any dual boot problems. And when you do have a dual boot and windows get infected by a virus/malware/spyware you don't need to reinstall everything and then run into any kind of problems.
If you run it in a VM and Windows does get infected, only thing you need to do is delete Windows from the VM and everything is deleted. Just be sure to backup everything you were working on ;) 
VirtualBox is a good and easy to use VM. On their site ([http://www.virtualbox.org](http://www.virtualbox.org)) you find installation instructions for Ubuntu.

---

### Post by YesWeCan on 2011-03-03
I like your washing powder box!

Regarding backups, VirtualBox has a feature called "snapshots" which stores the state of your Windows installation and all your files. Takes less than 30 seconds. You can then restore from any snapshot. It's quite wonderful. I don't think you can run Norton on a VB Windows but that is a good thing, IMO. I just use MS Security Essentials.

---

### Post by celldweller1591 on 2011-03-03
Virtual Box is a good option but you need a powerful system to get Windows working properly especially Photoshop inside Vbox. Be careful as all your work will be inside windows and i think you will not be able to access those files directly from ubuntu. Dual boot might possible harm your grub...so be careful with bot options...

---

### Post by 3Miro on 2011-03-03
If you want to run a windows app that requires fast performance or you want to run a 3D app (VirtualBox 3D technology is still considered experimental), then Dual-boot is the best. If your apps run well under VirtualBox, then use that, it is so much less hassle.

---

### Post by Ghost|BTFH on 2011-03-03
I use VirtualBox all the time, runs great and does exactly what I need it to (Mainly bring up a Microsoft OS so I can walk a client through issues they're having over the phone that are too simple to merit a house call).

I would suggest getting everything installed and set up - then just turning off its networking capabilities.  Set up a file share with your system so you have a spot you can safely toss items between the two OSes to get things done.  This avoids 99% of any risk of viruses and gives you a nice happy little Virtual Windows sitting in its own Linux terrarium.

Just a note - you do know that Linux has GIMP (I know, I know, it's not PHOTOSHOP) which does excellent photo editing and manipulation work...

As for Access - we have OOo Base (Soon to be replaced with LibreOffice Base) that does the same thing.

If those are your only two reasons for keeping Windows, perhaps studying those programs on your free time and learning if they can do the same job for you, might help you free up some more disc space later down the road. :)

Cheers,
Ghost|BTFH

---

### Post by humbug01 on 2011-03-03
Just to add my 2 cents.

> I would suggest getting everything installed and set up - then just turning off its networking capabilities. Set up a file share with your system so you have a spot you can safely toss items between the two OSes to get things done.

This is exactly what I do with WinXP running in VirtualBox in Ubuntu Lucid. It works great. The one main program I use is a 20 year old essential program that runs only in Windows (it does ancient Greek grammatical concordancing). Since WinXP has no internet access, I don't have virus software running in it in VB. I have snapshots and you can export the "appliance" as well. Works real slick.

While I also dual boot to WinXP, I never use it anymore except in VB....

Steve

---

### Post by garfonzo on 2011-03-03
Thanks for the great info folks! It is good to hear how you are all handling your unique situations. I think this will work with the suggestion made about turning off networking. 

@Ghost|BTFH: Ya, I know about Gimp and I tried really *really* hard to use it instead of Photoshop. I just couldn't achieve the same work flow efficiencies. As for MS Access, my office has some databases still running on it so if I need to fix something, I need Access specifically. We are moving to MySQL and a web front end, though so there is light at the end of that tunnel. 

Thanks again folks!

---

