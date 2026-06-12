---
title: "Screenlets and Python 3.0"
date: 2009-02-25
forum: Desktop Environments
---

### Post by ferspock on 2009-02-25
Hello,

I have installed latest Python 3.0 version. After that, Screenlets does not work.

If I try to start it from console, I have this message:

PRINT _("launching screenlet-daemon.py...")
      ^SyntaxError: invalid syntax, line 121

If I comment this line, a new message appears showing the same error in a different place (always referencing PRINT commands).

I have read that this version of Python is so diferent than 2.5, I think this is the reason for this problem.

Is it possible to force Screenlets to use previous version of Python? if not, how to uninstall Python 3.0?

I am a new Ubuntu user.

Thanks!

---

### Post by ajmorris on 2009-02-26
hi there,
Yes, you are correct, python is not backwards compatible with previous versions. Therefore, until screenlets is updated to use python 3.0 you will have to downgrade python. Are you using a python that you installed manually, or one from the repositories?

AJ

---

### Post by ferspock on 2009-02-26
Hi,

I have installed this version of Python manually, following intructions from Python web page. Now I can see that in Synaptics repository manager exists Python 3.0, but it is unmarked. I have a mark in versions 2.5 and 2.4. (I supose it was installed when OS installation)

I don't know how to uninstall this 3.0 manually.

Thanks

---

### Post by ajmorris on 2009-02-26
> **ferspock said:**
> Hi,

I have installed this version of Python manually, following intructions from Python web page. Now I can see that in Synaptics repository manager exists Python 3.0, but it is unmarked. I have a mark in versions 2.5 and 2.4. (I supose it was installed when OS installation)

I don't know how to uninstall this 3.0 manually.

Thanks

Could you please paste the link to the install instructions that you used? There are multiple ways to install a package, so it depends how you installed it as how to uninstall it :)

AJ

---

### Post by ferspock on 2009-02-28
Hi,

I used this from the README file that comes with the package:

    ./configure
    make
    make test
    sudo make install

Thanks!

---

### Post by ferspock on 2009-03-01
Hi again,

I have found some files referencing python 3.0 in folder /usr/local/bin/

I have renamed all these files and after rebooting I can see that my system is using python 2.5 and now Screenlets is working fine.

But I should like to remove all unnecessary files of python 3.0, but I don't know how to find a list of directories where it was installed.

I hope you can help me.

Thank you very much.

---

### Post by snova on 2009-03-01
In **/usr/local/bin**: 2to3 idle pydoc python3.0 python3.0-config smtpd.py

In **/usr/local/include**: python3.0

In **/usr/local/lib**: libpython3.0.a python3.0

Your installation might be a bit different.

It's odd that Screenlets stopped functioning, though- installing Py3K from source shouldn't break anything.

---

### Post by ferspock on 2009-03-02
Thank you,

I have found all these files and folders.

Yes, my installation for python 3.0 was different because I didn't use the repository manager. I did it from python web page, downloading the pack and installing it manually.

I tried to mark this thread as solved, but this option does not appear in the menu, if you can, please mark it. 

Thanks again.

---

### Post by snova on 2009-03-02
> **ferspock said:**
> Yes, my installation for python 3.0 was different because I didn't use the repository manager. I did it from python web page, downloading the pack and installing it manually.

No, that's not what I meant. If you found them all, then it was exactly the same as my own from-source installation. It's just that I can't think why such an installation would conflict with the existing one, so I wondered if something was different...

> I tried to mark this thread as solved, but this option does not appear in the menu, if you can, please mark it.

It's been disabled for now. See: [http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481)

---

### Post by ajmorris on 2009-03-05
sorry, wasn't able to get onto the forums for a couple of days... although you have already done it, instead of physically deleting the files from the custom version you compiled, then installing the ubuntu repo ones, for next time, you should run ```
sudo make uninstall
``` from the source directory (the folder where you ran the steps you outlined above) This will make sure to remove all the files.

Then install the one from the ubuntu repos.


AJ

---

