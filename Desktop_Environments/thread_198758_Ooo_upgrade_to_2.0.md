---
title: "Ooo upgrade to 2.0"
date: 2006-06-17
forum: Desktop Environments
---

### Post by dalani on 2006-06-17
Ok here goes: I successfully installed OpenOffice2 but the damn thing wont start up. First I uninstalled the old 1.1.3 version. Then, after converting all the *RPMS from the Ooo 2.0.2 download to *deb files , I installed the files with the dpkg command. 

The result: all the Ooo software are installed and with visible Openoffice icons in my menu. But Ooo does not startup with menu. I read the README files which advises inserting <unset SESSION ..> in the soffice startup script. I also beforehand, put myself in the users group and used vim to try update the DRI thing shown in your how-to. I doubt its a video driver problem and < /etc/X11/XF86Config-4> does not exist on my computer. SO what is preventing Ooo from opening??? (no pun intended)

---

### Post by dalani on 2006-06-18
Ok the solution courtesy of the Ooo forums was that alien screwed up perms. Solved by changing permissions
```
chmod a+xr /opt/openoffice.org2.0/program/soffice 
```

---

