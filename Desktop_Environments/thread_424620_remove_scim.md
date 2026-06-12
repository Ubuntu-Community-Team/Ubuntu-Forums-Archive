---
title: "remove scim"
date: 2007-04-26
forum: Desktop Environments
---

### Post by expatCM on 2007-04-26
I have an issue running a Thunderbird install script when scim is present on a machine.  scim seems to prevent completion of the install.

Does anyone know either how to stop scim from loading or how to remove scim?

I have tried to use the kill command, this can remove four running scim processes but there is a scim zombie which remains.  Unfortunately the zombie is activated during the install script running, that then puts scim in the system tray and this appears to cause a problem.

---

### Post by llamakc on 2007-04-27
Does thunderbird installed from the repositories not work?

---

### Post by expatCM on 2007-04-27
The repositories are at Thunderbird 1.5  I am sharing the mailboxes with a Windows machine where the latest release, Thunderbird 2.0 is installed.  To share the data you need to have the same version of Thunderbird installed on both .....

---

### Post by expatCM on 2007-04-27
ok ... so this one is now done ......

I used synaptic to remove scim and then ran the Thunderbird install script.  It worked.  The only headache I have now is working out how to install scim again exactly the way it was .......

---

### Post by rbmorse on 2007-04-27
What is SCIM and what does it do, anyway?  Beside break Thunderbird, I mean.

---

### Post by expatCM on 2007-04-27
SCIM is a really important program ....  it lets you write in character sets other than "English".  So if you only understand Chinese, Japanese, Korean, Thai, Arabic  for example you can use SCIM as the Input Method Editor.   

It works very well indeed.  A huge proportion of the world population does not use a letter based alphabet to communicate (instead they use characters which represent words). Others do not use an alphabet based on roman letters ....  so I think you will see how it fits :)

---

### Post by Najand on 2007-04-27
There is an old bug( better to say problem with using C++ libraries) with SCIM. It usually conflicts with Adobe Reader, Skype, Realplayer, Firefox and other commercial softwares. You can still runs your softwares using:
```

export QT_IM_MODULE=xim

```
every time before running other applications.

---

### Post by expatCM on 2007-04-27
an old bug ....?   hmmm ... well I have not seen it before with anything, only with the Thunderbird install script on Feisty.  In all other respects scim works and works very well.   I think the issue here is not scim, it is the Thunderbird install script which is written for the average machine in the West that has no need for an IME ..  :)

---

### Post by llamakc on 2007-04-27
> **rbmorse said:**
> What is SCIM and what does it do, anyway?  Beside break Thunderbird, I mean.

Surely you can research this yourself. Maybe help the OP and install the packages that create the problem and see if you can reproduce the problem?

---

### Post by expatCM on 2007-04-28
erm .... I think I have .... please read the thread.

---

### Post by Ripfox on 2008-03-16
SCIM is nothing but a pain in the *** on my machine. I wish to kill it.

---

