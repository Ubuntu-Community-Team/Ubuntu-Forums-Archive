---
title: "HowFrom?"
date: 2006-08-15
forum: Desktop Environments
---

### Post by sdebo on 2006-08-15
I decided to title this HowFrom instead of a HowTo as its is actually a bunch of queries which the noob (myself) thought would be straight forward but still cannot answer.

Please bear in mind that I have a windoz background so 'activate something' makes little sense.  Replies should usually spell out how things are done.  However I do prefer to learn the CLI version of commands and see what is happening under the hood.  GUIs are nice to ease work but only as long as I know what they are up to.

Before replying please note that **I already referred to a myriad of forum threads, but failed to find an answer to what I am asking below.**  

_Linux version:_ Ubuntu Dapper Drake

_Questions_

1) How do I launch XWindows from the console after I boot in recovery mode?

2) Prior to crashing my Ubuntu installation (reinstalling on other PC at the moment) I had a problem with a Live Value sound card which would work prior to login, and when accessed (alsamixer/aplay) as root through sudo command; but was not found when run under the default user account.  lspci did detect the card under both accounts however.  Any ideas?  File permissions maybe?  **I did install the physical soundcard after installing Ubuntu if that makes a difference.** 

3) After setting up Samba to access a folder on Linux from XP I got a host/Guest logon dialog asking for a password.  I edited smb.conf and synched the accounts with Linux.  Now should I create a Guest account?  Alternatively, why were my deafault username and password not accepted?

4) I shared a PSC1110 printer on XP.  It is visible to Ubuntu and print jobs do clear from the Linux print queue.  However they get stuck in the XP print spooler.  The printer leds just flash and not print job comes out.  What's the possible problem?

I plan to stick to Ubuntu but these teething problems are not making it a smooth ride.

Thanks for any help you can provide.

---

### Post by maniacmusician on 2006-08-15
> 1) How do I launch XWindows from the console after I boot in recovery mode?

Do you mean an xsession? I think what you're looking for is "startx". you will then have a normal graphical desktop.

dont know about the other stuff, sorry. didnt have those problems.

---

### Post by sdebo on 2006-08-15
Tried looking for something sensible under /usr/bin/X11 folder but there were too many files.

That one is sorted. Thanks:)

---

