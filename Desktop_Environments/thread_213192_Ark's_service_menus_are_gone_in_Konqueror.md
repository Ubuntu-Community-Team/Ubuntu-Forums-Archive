---
title: "Ark's service menus are gone in Konqueror"
date: 2006-07-11
forum: Desktop Environments
---

### Post by dangerous666 on 2006-07-11
Don't know what I did, but the Ark's service menus in konqueror desappeared... Actions like "extract here" , "extract to", and the compression ones are not available anymore... I have the package "konq-plugins" installed (previously, the ark's services menus were in this pack)... Does someone have any idea?

---

### Post by Jucato on 2006-07-11
You can try this:

1. Open up Konqueror and go to /usr/share/kubuntu-default-settings/kde-profile/default/share/mimelnk/application/
2. Either delete everything there or move them somewhere in your /home directory I prefer to copy them elsewhere, just in case I want them back. The FAQ recommended deleting them. Remember you have to actually remove or move those .desktop files. So you have to need root access.
3. Restart Konqueror

If you decided to just remove them, here's the easier way

From [http://www.kubuntu.org/faq.php#konqueror](http://www.kubuntu.org/faq.php#konqueror)
> 
To enable Konqueror to open tar and zip files:
```

rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/mimelnk/application/

```

---

