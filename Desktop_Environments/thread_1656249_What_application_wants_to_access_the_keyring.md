---
title: "What application wants to access the keyring?"
date: 2010-12-30
forum: Desktop Environments
---

### Post by atroq on 2010-12-30
Hi,

some weeks ago, I started getting the prompt from the keyring manager after each login:

Enter password for keyring 'Default' to unlock
An application wants access to the keyring 'Default', but it is locked

I don't know what I could have changed, but this is getting pretty annoying. I know that it is not the network-manager, it is configured for "all users" and my Wifi is working even when I cancel the dialog. In fact, canceling the dialog seems to have no effect at all.

Is there any way to find out which application might be trying to access the keyring (and to stop it from doing so)? I already tried disabling some of the startup applications (which seem to be all default anyway) but that didn't help.

Please note that I do NOT want to set an empty password for the keyring because I think protecting it is a good thing. I just want to be prompted for the password only when I use it.

Any ideas? Thanks in advance!

---

### Post by mcduck on 2010-12-31
What applicatons you are using?

It would be pretty hard to even try to list every program that stores their keys in the keyring.

Anyway, from the ones included in the default setup at least Evolution, Empathy, Ubuntu One, Network manager and Gwibber use the keyring. Nautilus does too, if you have any network drives configured. And of course Remote Desktop Viewer and Terminal Server Client.

Anyway, since it sounds like you are using automatic login you really could just as well set the empty keyring password. You only ever need to unlock the keyring manually if you use automatic login, which would make your whole desktop, including not only your keyring but also all your files and your user account, insecure. In that situation it really makes no difference if the keyring stores it's data in encrypted format or not, it's available for anyone who gets access to the machine anyway. ;)

The way I see it you either are concerned about your security, and protect your user account with a password. Or you don't care that much about security and use automatic login and can then just as well leave the keyring unencrypted. Anything between these options doesn't really make any sense.

---

### Post by atroq on 2010-12-31
Thanks for your reply.

The only apps I can think of that might be using the keyring are Ubuntu One and Tomboy notes, which I have set up to sync via Ubuntu One. However, I don't see any settings that would make them sync automatically when logging in. Also, Tomboy isn't started at login, and I get the prompt even when I disable Ubuntu One in the startup applications.

I am not using any of the other apps you have listed.

I am not using the automatic login, but I am not using the encrypted home directory because it makes recovery so much more difficult. So I still would like to protect my keyring file with a password.

I just can't believe that it's not possible to find out which application wants to open the keyring ... I already looked at pstree but that did not help. Couldn't there be some other tool, or a log file, that I could look at?

---

### Post by Roah Denmark on 2012-02-07
> **atroq said:**
> 
I am not using the automatic login, but I am not using the encrypted home directory because it makes recovery so much more difficult. So I still would like to protect my keyring file with a password.

I just can't believe that it's not possible to find out which application wants to open the keyring ... I already looked at pstree but that did not help. Couldn't there be some other tool, or a log file, that I could look at?

I am going to echo this thought, I would also like my machine to be tighter than a camels rectum in a sandstorm.

After a period of Windows hacking I am left dubious about entering my password into anything that just asks for it, especially if it ask anonymously. 

I have been running Unbuntu 11.10 for 2 days now. I'm baffled why Ubuntu doesn't have the ability to identify which application, I mean how hard can it be for the pop up to say something like 'Ubuntu One wants to access your keyring' why be so vague as to say '**an application**'

I am new to this, how do I know what applications have been installed, I just downloaded the whole thing from the Ubuntu download site.

---

### Post by kd4dii on 2012-02-07
Hi
     If you have Ubuntu one set to start on boot up it is probably the one that wants the keyring to open.  I had that happen too when I was using Ubuntu one and I stopped getting it when I was no longer using it.  A quich test would be going to system preferences stat up applications and unchecking Ubuntu one and do a reboot and see if that stops the keyring prompt.
     Hope this helps.


Bob

---

### Post by yagolf on 2012-02-07
> **kd4dii said:**
> Hi
     If you have Ubuntu one set to start on boot up it is probably the one that wants the keyring to open.  I had that happen too when I was using Ubuntu one and I stopped getting it when I was no longer using it.  A quich test would be going to system preferences stat up applications and unchecking Ubuntu one and do a reboot and see if that stops the keyring prompt.

Thanks for your contribution Bob. Yes, Ubuntu One seems to be one of the main applications asking for the unlocking of the keyring, but that misses the point because so is Banshee (in certain situations) and there are others, so I can only echo Roah Denmark's words when he says> I'm baffled why Ubuntu doesn't have the ability to identify which application
The point is that it is.

:guitar:

---

### Post by ayesha14 on 2012-02-07
If you have Ubuntu one set to start on boot up it is probably the one  that wants the keyring to open.  I had that happen too when I was using  Ubuntu one and I stopped getting it when I was no longer using it.  A quite test would be going to system preferences stat up applications and Chungking Ubuntu one and do a reboot and see if that stops the keyring  prompt.

---

