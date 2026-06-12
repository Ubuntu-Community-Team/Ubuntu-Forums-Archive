---
title: "Problem with msi installer in the winetools installation."
date: 2006-06-19
forum: Desktop Environments
---

### Post by w1z4rd on 2006-06-19
Im really trying hard to get dreamweaver to work on kubuntu (if anyone has any suggestions or useful links im all ears!), so Ive done the whole wine installtion thing with apt-get install wine (and all other relveant files that were in my multiverse)* _Edit_: Found out how to install dreamweaver [http://www.ubuntuforums.org/showthread.php?t=200305](http://www.ubuntuforums.org/showthread.php?t=200305)*

When I get to the MSI installer part of the wine tools installtion, the msi installer part breaks, and says, installation failed.

I googled a bit, and I found that you could install the file by following these instructions:

> 5.2 MSI

MSI is an installer by Microsoft that appears to replace Installshield. MSI's .msi files can be installed with a utility called "Windows Installer". You can download Windows Installer from this location: Download

You can install Windows Installer by typing wine instmsia.exe

Now add the following lines to the DllOverrides of "Default Settings" using winecfg:

"msi" = "native, builtin" "msiexec.exe" = "native, builtin"

Now type wine msiexec /i msifile.msi and the application will be installed.



But when I run that command I get the following error:

> w1z4rd@b0x:~/.wine/fake_windows/windows/system32$ sudo wine instmsia.exe
Password:
wine: could not load L"c:\\windows\\system32\\instmsia.exe": Module not found
[email]w1z4rd@b0x:~/.wine[/email]/fake_windows/windows/system32$
[email]w1z4rd@b0x:~/.wine[/email]/fake_windows/windows/system32$       

I have tried reinstalling wine, but that does not appear to have helped. Do I need to purge then reinstall prehaps?

---

