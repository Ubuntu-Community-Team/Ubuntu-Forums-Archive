---
title: "Remotely monitor computers on my home network"
date: 2012-12-16
forum: Desktop Environments
---

### Post by bryan.sailer on 2012-12-16
I am looking for a way to remotely view my children's laptops on my home network. I plan on monitoring them from my laptop running Ubuntu 11.10. One of the laptops is running Windows 7. I have tried Remote desktop but I was not given access to the machine. I am looking for ideas for solve this issue.

---

### Post by papibe on 2012-12-16
Hi bryan.sailer.

What edition of Windows 7 do they have?

IFAIK, only the Professional, Ultimate, and Enterprise editions can receive remote connections (using the Windows native capabilities).

Regards.

---

### Post by RitzBitzN on 2012-12-19
Install TeamViewer on the client computer(s) (free download ,[http://www.teamviewer.com/en/download/windows.aspx](http://www.teamviewer.com/en/download/windows.aspx)). Set it up with their instructions, and then on your computer go to login.teamviewer.com to connect like remote desktop. Hope this helps!

---

### Post by doxramos on 2012-12-19
Instead of teamviewer I would recommend running a VNC server on the Windows computers which will make it so the server can't shut down without the admin password, so they can't just exit out and you can also connect to a local IP rather then an external workaround and then you just use the native Remote Desktop Viewer in ubuntu. Standard RDP is not effective in the sense that if you log in under and RDP session opposed to a VNC session it's going to lock them out of their computer whereas with VNC you can see what's going on in real time.

---

### Post by cybergalvez on 2012-12-19
> **bryan.sailer said:**
> I am looking for a way to remotely view my children's laptops on my home network. I plan on monitoring them from my laptop running Ubuntu 11.10. One of the laptops is running Windows 7. I have tried Remote desktop but I was not given access to the machine. I am looking for ideas for solve this issue.

I do exactly this with VNC, just install it on their machine and then you can log in and veiw it at any time. BTW my kids know this is the deal, that I can log in and see what they are doing online at any time, I've never hidden it from them, I just told them that is the cost of 1) my buying them computers and 2) I pay for the internet.

---

### Post by bryan.sailer on 2012-12-19
I will try the VNC and see how that works I appreciate all of the assistance.

---

### Post by hardenqueen on 2013-11-13
> **bryan.sailer said:**
> I am looking for a way to remotely view my children's laptops on my home network. I plan on [[COLOR=#222222]monitoring them from my laptop[/COLOR]]("http://www.myjad.com/monitor-computer-activity.html") running Ubuntu 11.10. One of the laptops is running Windows 7. I have tried Remote desktop but I was not given access to the machine. I am looking for ideas for solve this issue.


Computer Monitoring Software to find out the truth about anyone's computer activity.

---

