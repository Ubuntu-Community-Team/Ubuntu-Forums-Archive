---
title: "Rsync system backup help"
date: 2009-05-03
forum: General Help
---

### Post by Legace on 2009-05-03
Hi guys. I want to install the ATi fglrx driver, but because of countless problems I've encountered with it in the past, I'd like to make a full system backup.

Could I use rsync to backup the entire system (excluding /boot, /proc, etc.) and then restore from recovery mode if I fail?

The command to backup would be
```
rsync -av --delete --exclude-from="exclude" / /backup
```

exclude would look like:
```
- boot/**
- proc/**
- dev/**
- lost+found/**
- sys/**
- media/**
- tmp/**
```

EDIT: Do I need those "-" marks.. So should it be like above or below:

```
boot/**
proc/**
dev/**
lost+found/**
sys/**
media/**
tmp/**
```

The command to restore would be
```
sync -av /backup /
```

Would this work? And should I include/exclude some other files in exclude.txt?

Thanks

---

### Post by unutbu on 2009-05-03
Yes, what you describe should work. 
Here are two suggestions:
[list]
[*] Remove the * from the paths in exclude.txt. With /boot/*, the /boot directory is created, but will be empty. Without the *, rsync won't create /backup/boot. 
[*] The restore command should be
```

sudo rsync -av --delete /backup /
```

The --delete would be useful here because the installation of the ATI driver might create files that do not exist in /backup. The --delete flag will cause rsync to delete files in / that do not exist in /backup.
[/list]

---

### Post by Legace on 2009-05-03
Ok thanks :)

---

