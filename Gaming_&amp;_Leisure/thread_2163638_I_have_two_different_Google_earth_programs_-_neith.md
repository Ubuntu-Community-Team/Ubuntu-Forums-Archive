---
title: "I have two different Google earth programs - neither works"
date: 2013-07-19
forum: Gaming &amp; Leisure
---

### Post by bmavbeard on 2013-07-19
I will try to make this as brief as possible.

1) I have searched for a solution and they were way too hard.  I really tried most didn't even answer my unique question.

2) Until recently (5 days ago) I had Jaunty.  I started using way back 2008/2009 and I had somehow installed Google earth back then
Well, I am dual-booting with windows and long story short I couldn't do a fresh install so I updated doing every single version until I got to 12.04 LTS and I stopped upgrading then.

3) In reading the other forums trying to fix my problem I installed a few necessary packages for Google Earth to run and I installed Google earth-stable by going to their website and download a .deb file? (whatever that means) and installing it through the Ubuntu Software Center.  In doing this I was hoping (praying) that it would ask about old versions of Google Earth and let me uninstall the old version.  Wrong.  

Now, I am stuck with 2 version, 1 really old and really bad one that is terrible and a newer one (earth-stable) that halfway works but gives me some kind of garbage message about video card not supporting the graphics when it works on Windows XP.

My question is there is no way that I can find to UNINSTALL the old version of google earth.  I can uninstall the new version I think through the software center.

The old version does not show up in softare center at all.  I am scared I broke my ubuntu.  PLease help.

---

### Post by bmavbeard on 2013-07-19
I still need help :(  Lots of looks but no replies.  Does anyone know how to uninstall an old version of google earth?  Just want to get rid of it.  Cannot do it through regular channel that I know of.  Thanks

---

### Post by bmavbeard on 2013-07-19
Will a moderator please move this thread to the Games and Leisure section?  Maybe I am not getting a response because it should be in a different forum?

---

### Post by Iowan on 2013-07-19
Moved by request.

---

### Post by dvdhudson33 on 2013-07-19
+1    ...  I'd also like to know how to uninstall Google Earth.

---

### Post by bmavbeard on 2013-07-20
> **dvdhudson33 said:**
> +1    ...  I'd also like to know how to uninstall Google Earth.

Ok, I guess I got frustrated because so many views and nobody offered any help at all.  :(  
I am the kind of person that doesn't stop though so I finally figured it out.  

I had two Google earth programs to get rid of.  First, I tried to remove the newest one that I had installed in an attempt to remove the old one.  There might be a way to do that in software center but I found something on my computer called computer janitor and thought what the heck does this thing do.  I guess it comes standard on ubuntu because I certainly didn't download it.  It seems to removes old/obselete packages and I guess anything I installed that is .deb (not sure but it also removed google chrome).  You can select or unselect what you want removed. I decided to let it do its job.  So computer janitor got rid of the newest google earth install.  

I got excited thinking maybe the old google earth was gone too.  Nope, still there when I searched in dash. However, I noticed a folder called google earth and it had lots and lots of files in it.  Wouldn't you know it one of them said uninstall.  I thought there is no way that it can be this easy.  However, I double clicked it and it was apparently executable in the terminal.  I watched it disappear before my eyes.  

So there you have it. I would suggest the following to try to remove:

1) Try Software Center first - look under the installed part (at the top) and under one of the subheadings you might can find it.  Maybe other at the bottom.

2) If that doesn't work try computer janitor (although it may want to remove other stuff).  You could always just deselect everything but that package to be removed.

3) see if there is a folder with the name of that program and see if there is an uninstall package in there.  

I know that I cannot be the only one out there so I hope this helps someone else.

---

