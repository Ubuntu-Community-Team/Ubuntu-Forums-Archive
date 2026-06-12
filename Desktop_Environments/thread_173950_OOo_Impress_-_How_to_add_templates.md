---
title: "OOo Impress - How to add templates?"
date: 2006-05-11
forum: Desktop Environments
---

### Post by Garyu on 2006-05-11
I have downloaded some templates to use with OOo Impress, but I can't figure out how to get them into the document.

First I went through the menu "File -> Templates -> Administrate" (I'm translating swedish names here, so I'm not sure this comes out correctly) and in that dialogue selected "My templates", right-clicked it and selected "Import template" and added the template I wanted to use. This makes it show in the list and when I check "~/openoffice.org2/user/template" the file has been copied there. However, if I close this window and open it again my template has disappeared from the list while still being in the directory. And if I go to "Format -> Design -> Load template" the list is completely empty. 

I tried looking in the Path settings, but it seems to be correct. I tried removing the reference to /usr... there for templates so only my home directory path was left, but that didn't help either. 

Also, I have NO templates. It says on the net that two templates should be included with OOo Impress, but I haven't even got those two. 

So I tried manually copying lots of files to "~/openoffice.org2/user/template". There are mostly ".sti"-files, but also some "otp"-files. None of them will show in OOo Impress. 

In the About-box it says OpenOffice 2.0 and at the bottom "openoffice.org2-core 2.0.1-0breezy1, sat jan 7 01:11:04 UTC 2006

---

### Post by xyz on 2006-05-11
Sorry if you've already thought about this but you could check this out:
[http://www.oooforum.org/forum/search.phtml?mode=results](http://www.oooforum.org/forum/search.phtml?mode=results)
I am quite new with 00 but I found knowledge on that site.
Hope it helps.

---

### Post by emgy on 2006-05-11
Try looking at this link and scroll down to the 8th May entry. There is some useful info about templates there.

[http://openoffice.blogs.com/](http://openoffice.blogs.com/)

I regularly visit this site - there is lots of help available for Open Office.

---

### Post by Garyu on 2006-05-11
No, this does not solve my problem. They say to do exactly what I have done. My problem is that it isn't working. 

I did find a strange solution though. If I run "sudo ooimpress2" everything with templates work fine. But I don't want to sudo just to run OOo Impress... Does anyone have a simple solution for this?

---

### Post by jemate18 on 2008-07-05
> **Garyu said:**
> No, this does not solve my problem. They say to do exactly what I have done. My problem is that it isn't working. 

I did find a strange solution though. If I run "sudo ooimpress2" everything with templates work fine. But I don't want to sudo just to run OOo Impress... Does anyone have a simple solution for this?

Hi! I know it's been a long while since you have posted this. But anyway, I run into similar problem of yours. I found a solution.

Put your .otp [impress template] files on this:
/home/[user]/.openoffice.org2/user/template

Then restart openoffice.org impress
When you create a new presentation, select **From Template** in the Wizard. Then click My Templates in the drop down menu. You should now be able to see your new templates.

If this solves the problem, please mark this post as SOLVED.

Thanks.
Jemate18

"Don't find time for learning, Make time for it now!"

---

