---
title: "Problem: keyboard layout is not visible"
date: 2006-12-23
forum: Desktop Environments
---

### Post by mcglnx on 2006-12-23
Dear All,

When I do open the keyboard layout under Edgy, I do not see anything. Just a big empty dialog box.

Does anybody ever heard about this?

Thanks,
Mcg

---

### Post by ultranet on 2006-12-25
ditto here. Smb., please log a bug.

---

### Post by URB@N on 2007-01-16
I had the same problem when I upgrade from Dapper to Edgy. Well in a forum i read discusing for a bug and the said to do the following link:

     sudo ln -s /etc/X11/xkb /usr/share/X11

  I went in /usr/share/X11 and there where a folder xkb allready. This folder wasnot link to /etc/X11/xkb, instead there was a link inside this folder (/usr/share/X11/xkb/xkb). So I renamed the first xkb folder to xkb_old and made the correct link and it worked. Now /usr/share/X11/xkb IS A LINK to /etc/X11/xkb and everythink works normal again...

  Try it but do not delete the old folder in case i am wong.

---

### Post by chpts on 2007-01-16
After today's update (January 16th 2007) the same thing happened to me (Been running Edgy for some time and It didn't happened before).

Fortunately URB@N's post fixed the problem, though partially: Now the keyboard model and layout are shown in KDE under Kcontrol->Regional and Accessibility->Keyboard Layout.

Unfortunately there's a behavior that didn't happened before the update : usually under vim Ctrl-[ acts as an Escape (I've grown accustomed to this shortcut, also It's faster than to reach for Esc). Now it doesn't do a thing (it registers both keys if pressed independently, but not at the same time).

Any Ideas?

BTW My keyboard is a "Microsoft wireless comfort keyboard 1.0A" and the keyboard model is set appropriately.

Thanks.

---

### Post by mcglnx on 2007-01-16
> **URB@N said:**
> I had the same problem when I upgrade from Dapper to Edgy. Well in a forum i read discusing for a bug and the said to do the following link:

     sudo ln -s /etc/X11/xkb /usr/share/X11

  I went in /usr/share/X11 and there where a folder xkb allready. This folder wasnot link to /etc/X11/xkb, instead there was a link inside this folder (/usr/share/X11/xkb/xkb). So I renamed the first xkb folder to xkb_old and made the correct link and it worked. Now /usr/share/X11/xkb IS A LINK to /etc/X11/xkb and everythink works normal again...

  Try it but do not delete the old folder in case i am wong.

I tried your tip - but this does not change anything for me.

I tried the following:
[LIST]
[*]Update the link using your tip
[*]Force Re-install of the package
[*]Restart the Keyboard indicator
[*]Restore back the original setup
[/LIST]

None of this worked for me!

BTW I do not have any Flag (only Text) may be this is linked?

Thanks for your help,
M/

---

### Post by vladatnyc on 2007-01-28
Has anyone figured out a solution to this i am having teh same problem....

---

### Post by optevo on 2007-02-08
Yep - same problem here. Tried fixing the links and this did nothing. Has anyone logged this as a bug?

---

### Post by mcglnx on 2007-02-08
Noyhing??? May be should we ask on other forum?

---

### Post by optevo on 2007-02-08
The bug has been reported here:

[https://launchpad.net/ubuntu/+source/xorg/+bug/58083](https://launchpad.net/ubuntu/+source/xorg/+bug/58083)

If you don't want to read all about the bug, just download all the debs at:

[http://people.ubuntu.com/~seb128/xorg-server-edgy-update](http://people.ubuntu.com/~seb128/xorg-server-edgy-update)

and

sudo dpkg -i *.deb

And I installed the updated packages on Edgy and they fixed the problem with no apparent side effects.

---

### Post by mcglnx on 2007-02-10
Thanks Optevo! It works:

Just did a  
```
wget -l1 -r  [http://people.ubuntu.com/~seb128/xorg-server-edgy-update](http://people.ubuntu.com/~seb128/xorg-server-edgy-update)
cd people.ubuntu.com/~seb128/xorg-server-edgy-update/
sudo dpkg -i *.deb
```

Thanks a lot!

---

