---
title: "Can you make Ubuntu desktop seem smaller?"
date: 2011-09-06
forum: Desktop Environments
---

### Post by GumpTron on 2011-09-06
This may be a strange request or maybe not, but after using Ubuntu for a while one thing I wish I could change is the feel of the desktop. For example, both Ubuntu and Windows 7 both say they are operating at 1680x1050, but for some reason Ubuntu's desktop just seems more crowded and not as small or as deep as Windows 7's.  

Can it be changed to feel/look smaller compared to the size of the screen? 

Thanks for any help you can offer :guitar:

---

### Post by aura7 on 2011-09-06
The icon size in ubuntu is a bit bigger than that of Windows 7, you can probably reduce the icon size to accommodate more icons.

To reduce icon size you can check this post.
[http://ubuntuforums.org/showthread.php?t=532891](http://ubuntuforums.org/showthread.php?t=532891)

---

### Post by GumpTron on 2011-09-06
ill try that, thank you :popcorn:

---

### Post by GumpTron on 2011-09-06
actually, it's the large sidebar that's the problem for me. can i make that smaller? I don't actually have any icons on the desktop, just the large bar on the left.

---

### Post by nothingspecial on 2011-09-06
Install and run compizconfig-settings-manager.

Find the ubuntu unity plugin section

Click the experimental tab

Then drag the launcher icon size slider all the way to the left.

---

### Post by GumpTron on 2011-09-06
thank you very much :guitar:

---

### Post by jlmcp on 2012-03-07
So, the directions make sense, but the solution doesn't work. I just tried this on both 11.10 and the new 12.04 beta. If I change the icon size from 48 down to 32, nothing happens. I've even restarted X and Ubuntu, still no change. 

Is there a special "commit changes" button I'm missing?

---

### Post by stinkeye on 2012-03-08
> **jlmcp said:**
> So, the directions make sense, but the solution doesn't work. I just tried this on both 11.10 and the new 12.04 beta. If I change the icon size from 48 down to 32, nothing happens. I've even restarted X and Ubuntu, still no change. 

Is there a special "commit changes" button I'm missing?
The change is instant.
Are you in the **ubuntu** or **ubuntu 2d** session?
```
echo $DESKTOP_SESSION 
```

> [COLOR="YellowGreen"]glen@Oneiric:~$[/COLOR] echo $DESKTOP_SESSION
ubuntu

---

