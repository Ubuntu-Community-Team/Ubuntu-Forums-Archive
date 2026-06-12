---
title: "Firefox3&gt;Toolbar/Customize options not saved"
date: 2008-12-10
forum: General Help
---

### Post by 222fbj on 2008-12-10
I have a newly installed ubuntu 8.10/64 system.  I have Firefox 3.04 and several extensions installed.  The attached screenshot shows the Firefox addons panel, and the 'customize toolbar' mode.  

Any advice re fixing these problems?
[LIST]
[*]Only basic buttons show in the add/buttons panel... no 'adaware' button or other extension buttons. 
[*]Changes to the toolbars are not retained.
[*]Bookmark Toolbar does not show bookmarks
[/LIST]

fyi...firefox 'about' info:    Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.4) Gecko/2008111319 Ubuntu/8.10 (intrepid) Firefox/3.0.4

Thanks

---

### Post by em4r1z on 2008-12-10
> **222fbj said:**
> Only basic buttons show in the add/buttons panel... no 'adaware' button or other extension buttons.
Changes to the toolbars are not retained.
Bookmark Toolbar does not show bookmarks
1. Those are the buttons you should see. To see the button of an extension: it must be able to add a button to the tool bar and you must enable this setting within the extension preferences.
2. Are you pressing 'Done' after your arrangements?
3. The Bookmark Toolbar shows the links within the *Bookmark Toolbar* _folder_ within your bookmarks.

---

### Post by 222fbj on 2008-12-10
Yes I am pressing Done.  The bookmarks toolbar folder has 100+ bookmarks that show up if I go thru the bookmark menu.  I am familiar with Firefox customization/buttons.  However, I am new to linux and thot there might be some permission/setup issue with my firefox profile.  I'm not sure what the problem is... but I'd like to know how to check the Firefox profile/permission file settings.

> **em4r1z said:**
> 1. Those are the buttons you should see. To see the button of an extension: it must be able to add a button to the tool bar and you must enable this setting within the extension preferences.
2. Are you pressing 'Done' after your arrangements?
3. The Bookmark Toolbar shows the links within the *Bookmark Toolbar* _folder_ within your bookmarks.

---

### Post by em4r1z on 2008-12-12
Firefox profiles are stored in the hidden folder /home/USERNAME/.mozilla/firefox
Close Firefox, delete your profile and see if the problem persists.

---

### Post by dalesd on 2008-12-12
Yeah, I have a similar problem.  I just want to add a "new tab" button to my toolbar.  I can add it just fine, but when I restart FF, it's not there.

This happened either after moving my /home directory to it's own partition or upgrading to 8.10.  I suspect it's a file permission problem, but I don't know which file(s) need what permissions.

---

### Post by Scubdup on 2009-02-03
New to Ubuntu and the forum. Came looking for a solution to this problem too.

I opened firefox, moved all my bookmarks into the file/edit/view toolbar, together with the address block. I clicked "done", and if I then close firefox and reopen it, my changes are not kept.

So this is just a bump, really, for the initial question.

(Loving Ubuntu by the way!)

---

### Post by Scubdup on 2009-02-04
Follow up

Because I am impatient and was worried I should have been looking for an answer myself rather than ask on here, I did some more digging.

The problem has been raised elsewhere:-

[https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/275408](https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/275408)
[http://ubuntuforums.org/showthread.php?t=975708](http://ubuntuforums.org/showthread.php?t=975708)
[https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/281348](https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/281348)

And appears to be a conflict between firefox extensions Tab Mix Plus and Ubuntu Firefox Modifications. Disabling one or the other is a workaround, but apparently the issue is being dealt with.

---

