---
title: "trouble with wine"
date: 2006-05-23
forum: Gaming &amp; Leisure
---

### Post by seb4131 on 2006-05-23
hi,
    I am hoping someone can help me i keep getting this error whenever i run wine cfg i have tried reinstalling but with the same result the program tells me to add a drive but when i do it is never recognised any help would be great

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
err:winecfg:load_drives GetVolumeInformation() for 'E:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'E:\' failed, setting serial to 0

i have tried to uninstall wine but this hasn't fixed the problem either is there any way of getting rid of the wine settings from a previous instalation and start again

---

### Post by polpak on 2006-05-23
[QUOTE=seb4131]
i have tried to uninstall wine but this hasn't fixed the problem either is there any way of getting rid of the wine settings from a previous instalation and start again[/QUOTE]


The settings/files for wine are stored in the .wine directory in your home directory. To remove them simply rm -rf ~/.wine

---

