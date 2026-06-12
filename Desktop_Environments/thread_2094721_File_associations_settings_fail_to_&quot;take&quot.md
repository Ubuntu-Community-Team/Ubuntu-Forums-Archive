---
title: "File associations settings fail to &quot;take&quot;"
date: 2012-12-14
forum: Desktop Environments
---

### Post by jtappin on 2012-12-14
With Kubuntu 12.04 LTS (KDE 4.8.5), whenever I try to change the file associations using the KDE Systems settings (e.g. to remove an old video player that was inherited from a Solaris system and which does not exist on Kubuntu). When I click on "Apply", the 'updating system configuration' progress monitor just loops endlessly and hitting "cancel" just causes the updated settings to be lost.

Has anyone else seen this problem and if so is there a fix or workaround?

One possibility is that there is a permissions issue as I used XFCE on that machine for a bit and I have seen cases of XCFE and KDE disagreeing about what are appropriate permissions for config files, but I don't know on which files.

I all else fails, where are user-defined file associations stored so that I can edit the file by hand?

---

### Post by mparillo on 2012-12-14
On my 13.04 Daily Build, I see System Settings > Common Appearance and Behavior > File Associations. Or do you *really* want to edit them by hand? Sorry, I see you tried that already.

---

### Post by SeijiSensei on 2012-12-14
> **jtappin said:**
> I all else fails, where are user-defined file associations stored so that I can edit the file by hand?

They appear to be in $HOME/.local/share/mimeapps.list.  My copy of that file looks like this:

```

[Added Associations]
application/vnd.oasis.opendocument.spreadsheet=libreoffice-calc.desktop;calc.desktop;gnumeric.desktop;kde4-ark.desktop;
application/x-extension-eml=thunderbird.desktop;
application/x-gnumeric=gnumeric.desktop;libreoffice-calc.desktop;
inode/directory=kde4-dolphin.desktop;kde4-gwenview.desktop;
message/rfc822=thunderbird.desktop;
x-scheme-handler/mailto=thunderbird.desktop;

[Default Applications]
application/x-extension-eml=thunderbird.desktop
message/rfc822=thunderbird.desktop
x-scheme-handler/mailto=thunderbird.desktop

[Removed Associations]
inode/directory=gnumeric.desktop;

```

Make sure your user has full read and write access to .config, .kde, and .local, and all their subdirectories and files.

---

### Post by jtappin on 2012-12-17
> **SeijiSensei said:**
> They appear to be in $HOME/.local/share/mimeapps.list.  My copy of that file looks like this:


Make sure your user has full read and write access to .config, .kde, and .local, and all their subdirectories and files.

In my system it's $HOME/.local/share/applications/mimeapps.list, but that doesn't help much as the application I particularly want to remove is listed under "Removed Associations", so I think that the control centre has made it that far but then there is some other place where things are really stored (an akonadi database?) that is not getting updated.

And yes, I do have read/write (and where appropiate execute) access to all the relevant directories in my home directory.

---

### Post by jtappin on 2012-12-19
Looks like it was some service had crashed. After the the last kernel upgrade:
a) The logout/shutdown button didn't work to reboot with the upgrade
b) After rebooting from the command line, the offending application had been removed and further changes seem to be OK.

---

