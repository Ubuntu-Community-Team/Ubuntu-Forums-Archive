---
title: "&quot;Enter password for the default keyring to unlock&quot;"
date: 2009-05-16
forum: General Help
---

### Post by clayton911 on 2009-05-16
When I try to get online at home using Ubuntu 9 I get the error "Thee application 'nm-connection-editor' (/usr/bin/nm-connection-editor) wants to access the default keyring, but it is locked"  I tried ever password I've ever used and it denies them all.  Now at Panera Bread where there's no password it gets right on.  Please help.  Also where is .avi support in Linux?  Thanks.

Clayton

---

### Post by bolter40k on 2009-05-16
The default movie player has .avi support if you are having problems and it does not support .avi files install vlc media player in the package manager it plays almost any media file

as for the keyring problem

try going into terminal and enter

```
top
```

then post back if you see the application there

---

### Post by bolter40k on 2009-05-16
you arent online but just be aware that i do not know if this will solve your problem or if it could potentially hurt your install id wait till someone else jumps in to help

before you try what im going to type be cautious as i do not know if it will effect your install

after typing top in the terminal 

type 

kill

then it will ask the i.d. number assigned to it you will see it in top

---

### Post by Joeb454 on 2009-05-16
Without looking (I don't have an Ubuntu machine here at the moment) I would say that going to System > Preferences/Administration and looking for the keyring manager application may help.

The password isn't the same as your normal login password (unless you set them to be the same). Without sitting at an Ubuntu machine I can't be much further help, sorry :(

---

### Post by lovinglinux on 2009-05-16
Since you are apparently new here, I would like to give you a tip. This subject is very common and there are tons of posts about it in the forums. To search for them you can use Google Site Search. This type of search, which includes a string for the web site you want to search, gives you only results related to the chosen site. For example you could search for "keyring unlock site:ubuntuforums.org". It will give [these results](http://www.google.com/search?q=keyring+unlock+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0).

You might solve your problem with this:

> **mcduck said:**
> 
Changing/removing the keyring password is quite easy to do (no need to remove the current keyring or mess with user accounts):

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

