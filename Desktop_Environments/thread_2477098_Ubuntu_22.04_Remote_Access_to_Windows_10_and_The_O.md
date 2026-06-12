---
title: "Ubuntu 22.04 Remote Access to Windows 10 and The Opposite"
date: 2022-07-14
forum: Desktop Environments
---

### Post by richramik on 2022-07-14
Hey Gang:

I have Windows 10 at work.  I run Ubuntu 22.04 at home.  

Occasionally, I will do work at home on my Ubuntu 22.04 system.  I will then need to be able to access my home machine from the Windows 10 machine at work.  Then there are those times when I do work on my Windows 10 machine and need to access it from my Ubuntu 22.04 machine.  

With the work situation as it is, I would like to remote in both directions: desk top control, file transfer, and such.  Desk top and file transfer are paramount.

What would be the best software to do this????  I will rule out TEAMVIEWER cost is not worth it, and I don't want to use Chrome Desktop.  Our IT company does not like Chrome and they don't speak Ubuntu.  I already checked in with them.

Please remember I am not a techno-user, just an average user.  Oh, I just remembered, both the Windows and Ubuntu systems have dual monitors as well.

Thanks and Stay Safe,
Rich Ramik

---

### Post by grahammechanical on 2022-07-14
I am also an average user. I know nothing about what you want to do. But I am curious. If you was using Windows 10 at home would your employer allow you to connect to the company network over the internet? I ask because I thought that opening a company network to internet access was an invitation to the network being hacked. And you want to access a particular work computer with permission to transfer files and such. Criminals would like to do the same, in my opinion.

Regards

---

### Post by yancek on 2022-07-15
I agree with the post above.  It is certainly possible but the first thing you would need to do is get permission from your employer.  I'm sure they have settings which will prohibit this and you would need to get that info from your employer and they probably won't agree to it.

---

### Post by ActionParsnip on 2022-07-15
You can use SFTP (Which you will get with SSH) to send and receive files to and from the Ubuntu system. What would you want to do on the desktop? What activities?

Ubuntu can use RDP to the Windows system if the networking is in place.

---

### Post by richramik on 2022-07-15
Primarily, I will be accessing work items started (LibreOffice Text and Calc documents, and vice-a-versa) but not completed.  I will then transfer the files as well.

---

### Post by ActionParsnip on 2022-07-15
You can mount the SFTP in Windows then edit the files using the local word processor. When you save it will save on the remote file system.

---

### Post by grahammechanical on 2022-07-17
Have you thought of using email to send the files back and forth? 

Some years ago I was working as a safety officer in a high street store. I wanted to create password protected PDF documents of accident reports which I would send to head office. The company computer running Windows did not have a PDF creator. So, I intended to email the raw data as a text file to my own email address. Then I would use Libreoffice to create the PDF document which I could then email to the store email account that I had access to. Then I left that company. Such is life!

Regards

---

### Post by richramik on 2022-07-18
Went down that path already.  They said nope.

---

### Post by richramik on 2022-07-18
Went down that path already.  They said nope.

---

### Post by richramik on 2022-07-18
Some of the files, particularly PDFs will exceed the limits for email.  Need to have the ability for file transfer.

---

### Post by richramik on 2022-07-18
In short, I need the capabilities of TEAM VIEWER, without the expense of TEAM VIEWER.

---

### Post by TheFu on 2022-07-18
> **richramik said:**
> In short, I need the capabilities of TEAM VIEWER, without the expense of TEAM VIEWER.

Everywhere I worked the last 30 yrs, doing that would get me fired.  Breaching the network is cause for termination.  For 2 jobs, I could be sent to jail for bypassing their security.

But I was allowed to put files onto flash media (in many situations, but not all) and transfer files using "sneakernet" between home and work at a few less secure companies.

Some work places setup VPNs for remote access. If they don't do that, then you should ask them to make it so.  At a minimal, you'll get an IT policy created.

There are many subtle reasons never to allow desktop-to-desktop access into/from work computers.

If you don't control the WAN routers, you won't be setting up a VPN or setting up a way for your home computer to access your work computer.  And I seriously hope that the opposite is prevented (work --> home) by your IT team.  There are many, many, issues.

What happens when the bad guys take over your work computer?  In some companies that didn't take security serious, they've had all the payroll money stolen. Or they've had oil pipelines shutdown impacting 40M people.  What happens in your company when your network is breached?

---

