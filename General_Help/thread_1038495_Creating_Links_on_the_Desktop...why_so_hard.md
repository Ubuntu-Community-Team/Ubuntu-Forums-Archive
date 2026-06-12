---
title: "Creating Links on the Desktop...why so hard?"
date: 2009-01-12
forum: General Help
---

### Post by xefialtis on 2009-01-12
Greetings...
Ok, here is the situation...
My boss asked me if there is a way in Linux to create a link that can be used to execute a "new message" from the email.
He has it working in Windows, using a URL file with a MAILTO line inside it.
This is actually the easy part.
I have a .desktop file on my desktop that contains all this info
> 
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Something Wicked This Way Comes
Type=Link
URL=mailto:efialtis@efialtis.com?Subject=[BUILDINFO{product code}]: {BuildID} [AdditionalBuildInfo] {Operation} - {Result/Status} &body=Example Deploy Email:  [BUILDINFO-NFS]: ft-0.96-1234 deploy to system test - starting. %0D %0DExample Test Status Email:    [BUILDINFO-SISU]: ft-0.96-3333 level 4 - staging tests started  %0D %0DExample Test Results Email:   [BUILDINFO-NFS]: ft-0.96-1234 level 2 - PASS
Icon=emblem-mail

But when I execute it, it brings up a new email message with the TO line of "///efialtis@efialtis.com" (no quotes)...

After playing with this for 2 hours, I figured it was time to ask why I cannot seem to create a desktop or other type of file that will allow me to execute a New Message from my default email program (in this case, Thunderbird - but this should work with any program)...

The create launcher thins is useless as the drop-down does not contain "link" but if I use "location" I get the same results as when I use the .desktop file...the TO line contains "///efialtis@efialtis.com"...

Is this just one of those situations where I can do something in Windows but not in Linux, or am I missing something obvious?

Thanks

---

### Post by Juffo-Wup on 2009-01-12
Try with an application launcher that executes the following command:

[PHP]xdg-email mailto:efialtis@efialtis.com?Subject="[BUILDINFO{product code}]: {BuildID} [AdditionalBuildInfo] {Operation} - {Result/Status} &body=Example Deploy Email: [BUILDINFO-NFS]: ft-0.96-1234 deploy to system test - starting. %0D %0DExample Test Status Email: [BUILDINFO-SISU]: ft-0.96-3333 level 4 - staging tests started %0D %0DExample Test Results Email: [BUILDINFO-NFS]: ft-0.96-1234 level 2 - PASS"[/PHP]

---

### Post by xefialtis on 2009-01-13
Unfortunately, it does the same thing...
I get 
> 
TO: ///efialtis@efialtis.com

SUBJECT: [BUILDINFO{product code}]: {BuildID} [AdditionalBuildInfo] {Operation} - {Result/Status} 

BODY: Example Deploy Email: [BUILDINFO-NFS]: ft-0.96-1234 deploy to system test - starting. D DExample Test Status Email: [BUILDINFO-SISU]: ft-0.96-3333 level 4 - staging tests started D DExample Test Results Email: [BUILDINFO-NFS]: ft-0.96-1234 level 2 - PASS

I don't want or need the "///" in front of the email address...

Oh, and Thanks for helping out...
Any other ideas?

---

