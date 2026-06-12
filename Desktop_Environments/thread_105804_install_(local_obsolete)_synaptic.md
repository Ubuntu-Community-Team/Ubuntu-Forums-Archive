---
title: "install (local obsolete) synaptic"
date: 2005-12-19
forum: Desktop Environments
---

### Post by missmoondog on 2005-12-19
i just added a couple repositorys to synaptic to check for updates to gstreamer and such. was quite the list! i have been just using the basic repos generated from here, [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic). after updating all the gstreamer items, i now have a list of them in the install (local obsolete) section of synaptic. are those the old files? can i remove them? will they be removed if the cache is cleared from the update history? the file versions in both columns are the same.

thank you

---

### Post by missmoondog on 2005-12-24
ok. at first i thought this might be an item on the one computer i updated after the original posting, but i have now updated all 5 machines and all 5 have the older gstreamer items listed in install (local obsolete). why are all those there?

thanks

---

### Post by missmoondog on 2005-12-31
what this? nobody can give me any insight into this?
what exactly are these,  install (local obsolete) files?

---

### Post by tomski on 2006-01-02
install (local obsolete) are just config files from a previous version of that software that are 'obsolete' due to the reason that that package has changed the syntax or layout of config files for the new version & they may just be old/outdated documentation that the package has left there in case you still require them, also i think if you manualy change a config file for a given application they too might get left behind (because of the md5 hash has changed) so you can keep for future use.
I think you can remove them but i would wait or keep a copy of them, then remove if all is well after that delete the copys.

Another way you might end up with these is if you choose to just 'remove' a package & not 'completly remove' a package.

Remember when you uninstalled a application in windows it would leave the folder and some files normally a .dat or the unwise.exe or changelog.txt files these too are 'local obsolete' files.

---

### Post by Hairy_Palms on 2006-01-02
install local obsolete are not just config files, they show any software that was install with dpkg instead of apt, but i have found software from some third party repos appear there aswell

---

### Post by tomski on 2006-01-06
WHOOPS
[QUOTE=Hairy_Palms]install local obsolete are not just config files, they show any software that was install with dpkg instead of apt, but i have found software from some third party repos appear there aswell[/QUOTE]


yes sorry you are correct the analagy i gave was for 'Residual config'

sorry to cause confusion ignore me

---

