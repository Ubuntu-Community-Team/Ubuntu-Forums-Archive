---
title: "Constant Disk Activty"
date: 2009-02-24
forum: General Help
---

### Post by mulluysavage on 2009-02-24
I am in the middle of setting up my new Ubuntu beauty and after installing drivers for some things, I now get *constant* disk activity no matter what. The disk activity light blink is also very regular and sort of fast. I figure this isn't really a great thing - but I don't know where to start?

---

### Post by DGortze380 on 2009-02-24
> **mulluysavage said:**
> I am in the middle of setting up my new Ubuntu beauty and after installing drivers for some things, I now get *constant* disk activity no matter what. The disk activity light blink is also very regular and sort of fast. I figure this isn't really a great thing - but I don't know where to start?

How much RAM do you have?
Can you post the output of top please?

Sounds like something is hogging your RAM causing you to utilize SWAP continually.

---

### Post by mulluysavage on 2009-02-24
Thanks for the reply.

I have 3.1 GB RAM. I dont see *any* swap happening in the system monitor.

I'm sorry, what do you mean by "output of top"?

***

see output of top next post

---

### Post by mulluysavage on 2009-02-24
Tasks: 142 total,   1 running, 141 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.6%us,  0.2%sy,  0.0%ni, 96.3%id,  2.8%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   3237760k total,   996644k used,  2241116k free,   146076k buffers
Swap:  9478308k total,       76k used,  9478232k free,   501720k cached
         
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                   
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                    
   15 root      15  -5     0    0    0 S    0  0.0   0:00.14 events/0                      
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                       
   56 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                     
   62 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                        
   63 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                  
  247 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                       
  301 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                       
  302 root      20   0     0    0    0 S    0  0.0   0:00.08 pdflush                       
  303 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                       
  344 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                         
 1765 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                 
 1766 root      15  -5     0    0    0 S    0  0.0   0:00.22 khubd                         
 1825 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                      
 1879 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0                         
 1887 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                       
 2619 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                   
 2302 root      20   0     0    0    0 S    0  0.0   0:00.08 pdflush                       
  303 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                       
  344 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                         
 1765 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                 
 1766 root      15  -5     0    0    0 S    0  0.0   0:00.22 khubd                         
 1825 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                      
 1879 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0                         
 1887 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                       
 2619 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                   
 2701 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                     
 2702 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                     
 2703 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                     
 2704 root      15  -5     0    0    0 S    0  0.0   0:00.08 scsi_eh_3                     
 2705 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4                     
 2706 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                     
 2817 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_7                     
 2819 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_8                     
 3234 root      16  -4  2448  844  464 S    0  0.0   0:00.26 udevd                         
 5287 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty                         
 5288 root      20   0  1716  512  440 S    0  0.0   0:00.00 getty                         
 5290 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty                         
 5292 root      20   0  1716  504  440 S    0  0.0   0:00.00 getty                         
 5294 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty                         
 5552 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/0                   
 5629 syslog    20   0  1936  648  512 S    0  0.0   0:00.02 syslogd                       
 5685 root      20   0  1872  536  444 S    0  0.0   0:00.06 dd                            
 5687 klog      20   0  3684 2556  424 S    0  0.1   0:00.12 klogd                         
 5709 messageb  20   0  2832 1216  800 S    0  0.0   0:00.22 dbus-daemon                   
phil@mediabot:~$

---

### Post by DGortze380 on 2009-02-25
Well, you don't appear to be using swap much.

---

### Post by handy on 2009-02-25
For what ever reason so much of that RAM must be going to waste.

---

### Post by wowbagger53 on 2009-02-25
From the output of top:

> 2701 root 15 -5 0 0 0 S 0 0.0 0:00.00 scsi_eh_0 
2702 root 15 -5 0 0 0 S 0 0.0 0:00.00 scsi_eh_1 
2703 root 15 -5 0 0 0 S 0 0.0 0:00.00 scsi_eh_2 
2704 root 15 -5 0 0 0 S 0 0.0 0:00.08 scsi_eh_3 
2705 root 15 -5 0 0 0 S 0 0.0 0:00.00 scsi_eh_4 
2706 root 15 -5 0 0 0 S 0 0.0 0:00.00 scsi_eh_5 
2817 root 15 -5 0 0 0 S 0 0.0 0:00.00 scsi_eh_7 
2819 root 15 -5 0 0 0 S 0 0.0 0:00.00 scsi_eh_8 

I see that scsi_eh_3 has used 8 seconds of CPU. I believe that scsi_eh is a SCSI error handler, so perhaps this indicates that one of your discs actually has a problem.

---

### Post by mulluysavage on 2009-02-25
> **wowbagger53 said:**
> From the output of top:

 

I see that scsi_eh_3 has used 8 seconds of CPU. I believe that scsi_eh is a SCSI error handler, so perhaps this indicates that one of your discs actually has a problem.

Is there a utility that could help me check my discs?

---

### Post by mulluysavage on 2009-02-28
I found a couple of command-prompt utilities, but I'm much more comfortable using gui right now. Does anyone have any suggestions for a disk utility to check my HD health? Thanks!

---

### Post by meinzy on 2009-03-02
I've had the same problem with constant disk activity.  I've searched multiple posts for hours trying to fix.  No avail.  Then I noticed that when I put a disk in my DVD player it stopped.  I have no idea why.  I now keep a blank cd in my DVD player for a workaround till someone finally fixes this bug.  Hope this jury-rig helps.

---

### Post by mulluysavage on 2009-03-03
Thanks Meinzy, I tried your workaround but putting a cd in my drive doesn't help. It's wierd because it's not causing me a 'problem,' in other words, system resources don't seem too taxed, but I can't tell the difference because I haven't been able to get it to stop at all. Also I worry about long-term effects on my disk.

Does anyone out there know a good gui disk utility?

---

