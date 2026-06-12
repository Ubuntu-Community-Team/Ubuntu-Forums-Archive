---
title: "Customize Evolution toolbar?"
date: 2008-11-05
forum: Desktop Environments
---

### Post by quirks on 2008-11-05
Simple question, but I can't find the answer:
Is there a way to add/remove buttons in the toolbar of Evolution? Specifically, I would like to add a "Mark as Unread" button to it. I apologize, if the answer is obvious, but while googling and searching the forums, all I could find, is a post with no replies ([http://ubuntuforums.org/showthread.php?t=399373](http://ubuntuforums.org/showthread.php?t=399373)).

Thanks.

---

### Post by habl on 2008-11-05
I'm not sure, but I'm affraid it ain't possible. Atleast their isn't a configuration dialog for the toolbar. I searched for the xml files of evolution but couldn't find anything for the toolbar. You could sniff around in /usr/share/evolution/2.xx/ (change xx to your Evolution version number), maybe you have more luck.

---

### Post by quirks on 2008-11-05
Thank you for this valuable hint! I found a file /usr/share/evolution/2.22/ui/evolution-mail-message.xml. At the bottom there is a section
```
<dockitem name="Toolbar">
<!-- ... toolbar buttons ... -->
</dockitem>
```
I manually added the button there (after making a backup of the original file, of course). Unfortunately, Evolution does not load the icon, although there is an icon of the needed size in /usr/share/icons/gnome/24x24/actions.

But still, thank you. At least, one is able to remove buttons, without any issues, this way.

---

### Post by BenTX on 2011-08-17
I second this; having grown accustomed to the "Mark as unread" button in Outlook, especially in individual email messages...

---

