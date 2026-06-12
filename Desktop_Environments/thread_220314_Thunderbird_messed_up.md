---
title: "Thunderbird messed up"
date: 2006-07-21
forum: Desktop Environments
---

### Post by shane2peru on 2006-07-21
Ok, I ran ```
sudo mozilla-thunderbird
``` so I could install dictionaries in thunderbird.  When I restarted thunderbird, it wants me to setup a new account now.  I'm sure that it changed all my permissions for my files to root now.  How can I fix this?  I know there is a chmod command, but I'm not real familiar with it, and not sure what the proper settings should be for my thunderbird files.  Help!](*,) 

Thanks,
Shane

---

### Post by mannheim on 2006-07-21
You could try

```

sudo chown -R joe:joe /home/joe/.mozilla-thunderbird

```

to change the owner of all files and directories at or below ~joe/.mozilla-thunderbird to "joe". 

BTW, I think the standard spelling dictionaries for thunderbird are in the repostitories; so you can install them that way, unless you had something more particular that you needed.

---

### Post by shane2peru on 2006-07-21
> 
Code:

sudo chown -R joe:joe /home/joe/.mozilla-thunderbird


didn't work.  I did manage to get it fixed. I re-setup a new account like they wanted.  
  In - /.mozilla-thunderbird/8ajdjkuad98.default/Mail/  it had duplicated folders.  I just copied the old ones with all my settings into the new ones it made (with the same names-1) and presto everything was back to normal.  

  The reason I tried running it with sudo was I heard that would help install dictionaries, since it didn't work when run normally as a user.  I found it best just to ```
sudo apt-get install myspell-es
```  That seemed to install the dictionary I needed for Thunderbird (es being "Español").  Hope this helps someone else.

Shane

---

