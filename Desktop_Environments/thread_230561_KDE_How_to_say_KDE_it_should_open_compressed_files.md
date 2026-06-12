---
title: "KDE: How to say KDE it should open compressed files with Konqueror?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by TTL on 2006-08-06
Hello,
since upgrading to Dapper KDE opens compressed files (.zip .tar.gz .tar.bz2) always with Ark, if clicking on such a file. I prefer it if they were opened within Konqueror again, using the zip:/ tar:/ protocols. I can manually enter the address in the address-bar like zip:/home/foo/bar.zip but did not figure out how to say it KDE to do so on a mouse click.

I tried to modify the mime type eg. application/x-tgz. In the 'embedded' tab the setting is 'open in embedded viewer' but the list of programs below is empty. On other computers (with an older Kubuntu Version) there is the program 'ark_part' in this list. I tried to add 'ark_part' on mine as well but there is no such program 'ark_parts' selectable in the 'Add' list.

Hope someone could help me.

---

### Post by Jucato on 2006-08-06
go to /usr/share/kubuntu-default-settings/kde-profile/default/share/mimelnk/application and move or delete the contents of that folder. These are MIME links for archives.

Hope that helps.

---

### Post by TTL on 2006-08-06
Thanks, moving the MIME links to an other place did exactly what I wanted :)

---

