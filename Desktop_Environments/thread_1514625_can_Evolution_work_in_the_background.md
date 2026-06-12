---
title: "can Evolution work in the background ?"
date: 2010-06-21
forum: Desktop Environments
---

### Post by AM_SOS on 2010-06-21
hullo,
i recently setup Evolution to work with gmail on 10.04.
everything is working fine, except one little "feature" which i am not sure is working ok. if it is it can only be called pretty badly implemented !
for gmail, evolution is supposed to inform the user as soon as a new mail arrives in the inbox. however, i have noticed that its unable to do so unless i am logged on into Evolution in its browser window. in other words, it seems that there is no possibility of it working in the background and informing me of incoming mail by a pop up, sound etc. all of this it does but only if it is open in its browser window, though again there is no sound here.
is this due to improper configuration or a "feature" of Evolution?
anyone ?

---

### Post by holden448mex on 2010-07-04
I would like to know too. I have gone through the menus and the options and I haven't seen any option to make it work in the background.

---

### Post by sgosnell on 2010-07-04
Evolution must be open to work.  It is not a daemon, it's a full app.  If you just want to be informed of incoming mail, use one of the gmail notification daemons, of which there are several.  Putting "gmail notification" into a Google search box will get a long list.  After the notification, you'll have to open Evolution or a browser window to read the message, the notifiers just tell you there is a message, they're not email readers.

Evidently there is a daemon for Evolution, and for Ubuntu in general, and they may not be completely compatible.  Read [this thread ](http://ubuntuforums.org/showthread.php?t=1311909&page=2) for more information which might be helpful.

---

### Post by ThomasB2k on 2010-07-04
Although it will eat up a bit more of your RAM, you could always put Evolution on a different virtual desktop and leave it open. Then you will be notified of new mail.

---

### Post by AM_SOS on 2010-07-05
thanks all,

however i have since realized that evolution is not really useful for my purposes which include checking email from a few accounts.

i have of course already installed it. so if i go to the software centre (or synaptics) and uninstall the relevant packages will this effect other applications such as chat ?

any other issues that i need to be careful with while uninstalling it ?

thanks!

---

### Post by ankit singh on 2010-07-05
CheckGMail is the best of all.It looks for your message every user defined intervals all also displays the message contents.Here is the screenshot

---

### Post by sgosnell on 2010-07-05
Evolution is installed by default.  You can uninstall most of it, maybe all.  Just make sure to check what is going to be uninstalled before you commit to it.  If you just want an email client, Thunderbird may work better for you.  It's in the repositories.

---

