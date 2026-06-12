---
title: "Locate email with a virus in Thunderbird inbox file"
date: 2009-01-07
forum: General Help
---

### Post by VictorR on 2009-01-07
I scanned my home folder for viruses and got notification about two viruses in Thunderbird inbox files. I want neither delete nor put them into a vault, as these are single files  containing all my emails.

Any ideas how to locate the infected emails, so I could just delete them in Thunderbird?

---

### Post by geofff on 2009-06-07
I've just had the same problem. What I did was to set up message filters to transfer over groups of messages to a test folder that I had set up. I transferred over about half then ran clamav on both the test and the inbox. Then transferred more and more, again testing with clamav. Finally, having tranferred everything over to the test box, the inbox was still showing infection with trojan 14 but the test box was clear. 

I also had a similar infection in the junk box and the deleted box. After deleting all the files from the deleted box that infection went but even after deletion of all files from junk that box still showed an infection.

Therefore manually removed the now empty inbox and junk box from my Local Folders file and tested again. The offending trojan had gone. 

When new emails arrived these automatically set up a new clean inbox and junk box.

I then transferred all the previous inbox emails back to where they'd come from using message filters run on my test box. The process was very messy and time consuming but the only way I could find. Using message filters did however speed up the process. I've now set up automatic scanning of incoming mail using clamdrib which seems to be working well although its yet to find anything, so I'm not sure how this works yet. Instructions for this are at [http://ubuntuforums.org/showthread.php?t=885261&highlight=thunderbird+virus]("http://ubuntuforums.org/showthread.php?t=885261&highlight=thunderbird+virus") but make sure to also load the clamav-daemon.

---

