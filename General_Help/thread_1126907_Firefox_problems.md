---
title: "Firefox problems"
date: 2009-04-15
forum: General Help
---

### Post by 24601oxy on 2009-04-15
I've recently been having some of problems with Firefox recently. This might be the wrong place to go, but I figured I'd start here. 

The biggest problem is that it isn't rendering pages properly, including this one. Its screwing up the formatting on some pages, with no background, few images, and content all over the place. It isn't all of them though, and some are lodaing just fine.

I tried seeing if updating the system would help, so I ran the updates, including a few Firefox ones. When I opened it back up, all my bookmarks were gone. I think the rest of my settings might be gone, too. Also, my back buttons won't click. 

IDK if the two are related, but does anyone have any advice?

---

### Post by maheshasolkar on 2009-04-15
Are you using any Firefox add-ons? Which ones?

Can you try to invoke firefox in safe mode:

```
  firefox -safe-mode

```

Now see of the pages render any better? If things are better, some add-on is probably the culprit. Try disabling one add-on at a time and try to narrow down to one. If you find it, it will be much easier to find a solution.

Very often, if you use an over-zealous wildcard in add-ons like adblock, pages may be messed up.

---

### Post by 24601oxy on 2009-04-15
Well, that seems to have fixed the rendering. All I had as an add-on was a twitter client though.

Any ideas on the lack of bookmarks? They show up when I start typing them, but not in the toolbar or menu.

Also, I forgot about this with the bigger problems, but the search bar isn't working... it won't submit a search.

---

### Post by codeseer on 2009-04-15
> **24601oxy said:**
> Well, that seems to have fixed the rendering. All I had as an add-on was a twitter client though.

Any ideas on the lack of settings?

Try disabling that one addon and restarting Firefox normally. See if it continues outside of safe mode. If it doesn't, then the addon is at fault. If it does continue, then I would recommend a new profile.

```

firefox -profilemanager -no-remote

```

---

### Post by 24601oxy on 2009-04-15
Is there something I have to do to disable it? 

When I close it and re-open it, it runs a scan of my add ons for compatibility. It seems to do this every time, and takes me to the "firefox has updated screen". 

When I tried to open the add ons menu, the program crashed.

---

### Post by codeseer on 2009-04-15
> **24601oxy said:**
> Is there something I have to do to disable it? 

When I close it and re-open it, it runs a scan of my add ons for compatibility. It seems to do this every time, and takes me to the "firefox has updated screen". 

When I tried to open the add ons menu, the program crashed.

Yes. To disable it, go to the Tools menu at the top of Firefox, click 'Add-ons', click on the addon, click 'Disable', then close everything out and launch Firefox again.

---

### Post by 24601oxy on 2009-04-15
Sorry, I meant safe mode. 

And opening the add ons menu has the problem of crashing the program.

---

### Post by codeseer on 2009-04-15
Just try ditching the profile for now and try it under a new profile.

```

firefox -profilemanager -no-remote

```

Create a new profile in the window it gives you, click on the new profile and run it.

---

### Post by 24601oxy on 2009-04-15
I get the following error message:

```
Profile couldn't be created. Probably the chosen folder isn't writable.
[Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIToolkitProfileService.createProfile]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: chrome://mozapps/content/profile/createProfileWizard.js :: onFinish :: line 233"  data: no]
```

---

### Post by codeseer on 2009-04-15
Check the permissions on the .mozilla folder in your home directory.

---

### Post by 24601oxy on 2009-04-15
I don't really know what it should look like...

---

### Post by codeseer on 2009-04-15
> **24601oxy said:**
> I don't really know what it should look like...

Well if you look at it from the command line:

```

ls -al | grep mozilla
drwx------  5 username username   4096 2009-04-03 21:18 .mozilla

```

If you right-click the .mozilla folder and go to properties, then click the permissions tab, then you should check that you are the owner, folder access is set to 'create and delete files' and 'allow executing as program' has a line through it.

---

### Post by 24601oxy on 2009-04-15
Terminal says 
```
drwx------   6 oxy  oxy        1024 2008-04-25 19:25 .mozilla

```

and the permissions tab *looks* right.

---

### Post by HOLOGRAPHICpizza on 2009-04-15
Try running
```
chown -R $USER: .mozilla
chmod -R 664 .mozilla
chmod -R 775 .mozilla/*/
```
That should fix up all the permissions in your mozilla folder.

And if nothing works, you can always get a clean slate by doing
```
rm -Rf .mozilla
```

---

### Post by 24601oxy on 2009-04-15
I got this:

```
oxy@RivenDell:~$ chown -R $USER: .mozilla
oxy@RivenDell:~$ chmod -R 664 .mozilla
chmod: cannot access `.mozilla/firefox': Permission denied
chmod: cannot access `.mozilla/mozver.dat': Permission denied
chmod: cannot access `.mozilla/plugins': Permission denied
chmod: cannot access `.mozilla/appreg': Permission denied
chmod: cannot access `.mozilla/pluginreg.dat': Permission denied
chmod: cannot access `.mozilla/default': Permission denied
chmod: cannot access `.mozilla/extensions': Permission denied
oxy@RivenDell:~$ chmod -R 775 .mozilla/*/

```

And if I do rm -Rf .mozilla, will I lose all my bookmarks etc?

---

### Post by codeseer on 2009-04-15
Try it with 'sudo'.

---

### Post by HOLOGRAPHICpizza on 2009-04-15
Yeah, prefix the commands with sudo.

And if you do the rm command, you will loose all of your firefox settings, bookmarks, and stuff.

---

### Post by 24601oxy on 2009-04-16
Um... I think somehow the contents of that folder got deleted or something? I can't open firefox. 

[I'm typing this from a differnt browser]

---

### Post by codeseer on 2009-04-16
> **24601oxy said:**
> Um... I think somehow the contents of that folder got deleted or something? I can't open firefox. 

[I'm typing this from a differnt browser]

The actual binary isn't under .mozilla; just the user's settings, plugins, addons and profiles.

Edit:

I think Firefox would still start, even if you deleted .mozilla.

Edit 2:

Yeah, I just verified it in VirtualBox. Just send .mozilla to the trash and start Firefox back up.

---

### Post by 24601oxy on 2009-04-16
Still not opening...

---

### Post by codeseer on 2009-04-16
No errors when trying to open it from a terminal?

What do you get when you do: 'tail -F /var/log/messages'?

Edit:

I just did a 'complete removal' of the 'firefox' and 'firefox-3.0' packages in synaptic; then marked 'firefox' for installation and reinstalled it. 'ubufox' left some residual configuration, so I removed that. I then deleted the .mozilla directory. That didn't break anything in my VirtualBox, so that could be an option to try out.

---

### Post by 24601oxy on 2009-04-16
Firefox won't open in terminal. No error message, it just doesn't open. 

However, when I opened some other programs in terminal, it gives an error message like: 

```
oxy@RivenDell:~$ openoffice
sed: couldn't flush /home/oxy/.openoffice.org2/user/basic//sedhVFM75: No space left on device

```

or 

```
oxy@RivenDell:~$ transmission
Couldn't read "/home/oxy/.config/transmission/settings.json": Success
Couldn't save file "/home/oxy/.config/transmission/settings.json": No space left on device

```

By now, I'm working out that this isn't just local to firefox. Somehow, my HDD, which I thought was less than half full (not totally sure, I don't recall the time I checked.) I don't *think* I could have filled it up. But maybe I did? Too many torrents maybe... 

Also, I tried to make a home user backup earlier in the week, but it didn't write to the DVD I had in (I'd never tried doing that before). Could it have written to my HDD?

```
oxy@RivenDell:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6            110464595 105086812         0 100% /
tmpfs                  1031664         0   1031664   0% /lib/init/rw
varrun                 1031664       316   1031348   1% /var/run
varlock                1031664         0   1031664   0% /var/lock
udev                   1031664      2800   1028864   1% /dev
tmpfs                  1031664       104   1031560   1% /dev/shm
/dev/sda3               197599     57712    129847  31% /boot
overflow                  1024        32       992   4% /tmp
tmpfs                  1031664      2004   1029660   1% /lib/modules/2.6.27-11-generic/volatile

```

---

### Post by codeseer on 2009-04-16
From the looks of it, it's full.

---

### Post by 24601oxy on 2009-04-16
OK, I feel really stupid now. 

Somehow, when trying to extract a .rar, it made over 100 copies of it. I sent all those to the trash, but neglected to empty it. I just deleted 30 GB. 

Everything seems to be running fine... except all my firefox bookmarks and settings are gone for good, I'd guess.

---

### Post by codeseer on 2009-04-16
No idea how that happened?

---

### Post by 24601oxy on 2009-04-16
not really. 

At this point, I can live.

Now that I know whats wrong, it looks like a load of people have had the original problem. Not sure why my .mozilla folder was emptied, though.

---

