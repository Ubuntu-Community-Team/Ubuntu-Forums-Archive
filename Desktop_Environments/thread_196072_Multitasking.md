---
title: "Multitasking?"
date: 2006-06-13
forum: Desktop Environments
---

### Post by xfile087 on 2006-06-13
I'm running Ubuntu 6.06 on an AMD Athlon 64 3200+ clocked at 2GHz with 1GB of RAM and SATA drives... YET

Windows XP (got rid of it now) - I could rip CDs, use 3D applications, Photoshop CS2 etc etc and have no slowdown.

On Ubuntu... I rip a CD to my HD and it practically comes to a halt while it rips. Can this be right?

Just to be clear, my computer slows down, not the ripping speed.

Any suggestions on why or how to fix would be much appreaciated!

---

### Post by mattkenn4545 on 2006-06-13
Is DMA enabled on the CD-ROM drive?

If not look at the WIKI for enabling DMA and follow those instructions

---

### Post by xfile087 on 2006-06-13
Yep, it's on. I checked (though I read somewhere Dapper enables it by default).

---

### Post by johnc4510 on 2006-06-13
To enable DMA do this:
Applications>Accessories>Terminal
Copy and Paste the following line by line:
sudo hdparm -d1 /dev/hdd            
sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup
sudo gedit /etc/hdparm.conf

Now add the following lines at the end of the page:
/dev/hdd {
dma=on
}

Hit the save on the tool bar
type exit in terminal window

---

### Post by IcemanV9 on 2006-07-18
HP Pavilion ze5185
512 Mb RAM (847 Mb Swap)
ATI Radeon Mobility M6 LY

I thought _multitasking_ was one of Linux's strength. It was NOT up to par. I was running Apple HD movie trailer AND playing tour on Google Earth at the SAME time. The trailer jerked A LOT and the tour went slower than usual. What's going on?

---

