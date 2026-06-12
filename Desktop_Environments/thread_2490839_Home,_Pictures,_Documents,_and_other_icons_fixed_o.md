---
title: "Home, Pictures, Documents, and other icons fixed on desktop"
date: 2023-09-18
forum: Desktop Environments
---

### Post by tapasray on 2023-09-18
I am running Ubuntu 22.04.03. After installing the latest updates, I find icons of Home and its sub-directories, such as Pictures, Documents, etc., appearing on the right side of my desktop, and I am unable to make them disappear through anything in Settings>Appearance. I need help with this.

Thanks in advance.

---

### Post by yancek on 2023-09-18
The link below explains how to remove the /home icon from the Desktop.  Check to see if you have that option with a right click on the Desktop.  l I don't know if that will also remove the sub-directories and files.  Try it and make note of what you do so you can change it back if it does not do what you want.  Seems like unusual behavior to me and I don't know why a simple update would do that.  I'm not using 22.04 so...? 

[https://itsfoss.com/ubuntu-remove-home-icon/](https://itsfoss.com/ubuntu-remove-home-icon/)

---

### Post by tapasray on 2023-09-18
Thank you. Will try it and see.

---

### Post by tapasray on 2023-09-18
As you had anticipated, only Home could be hidden. 

Then I thought I would open Desktop in 'Files' and use the latter's 'Hide' functionality to hide the desktop icons. But, as you will see in the attached screenshot, links to Desktop and other directories are broken.

---

### Post by yancek on 2023-09-18
Those should not be links as everything in the image in your last post are default directories, the mozilla.pdf excepted.  If you run the command below, do you see the appropriate directories?  The error message in your image on the last post says the directory Desktop does not exist?

```
ls -l /home/tapas 
```

---

### Post by #&amp;thj^% on 2023-09-18
> **tapasray said:**
> I am running Ubuntu 22.04.03. After installing the latest updates, I find icons of Home and its sub-directories, such as Pictures, Documents, etc., appearing on the right side of my desktop, and I am unable to make them disappear through anything in Settings>Appearance. I need help with this.

Thanks in advance.

See this: [https://ubuntuforums.org/showthread.php?t=2490722&p=14157705#post14157705](https://ubuntuforums.org/showthread.php?t=2490722&p=14157705#post14157705)

---

