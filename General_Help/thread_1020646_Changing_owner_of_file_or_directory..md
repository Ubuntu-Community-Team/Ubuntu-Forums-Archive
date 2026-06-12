---
title: "Changing owner of file or directory."
date: 2008-12-24
forum: General Help
---

### Post by Janeleaper on 2008-12-24
Ubuntu 8.04.

I've downloaded ecofont and want to install it in Open office. The instructions are: 

1) Create a directory to hold your "misc" fonts under /usr/share/fonts. Can be /usr/share/fonts/miscttf. Copy ttf file to it.
2) Run the following commands:
ttmkfdir mkfontdir fc-cache /usr/share/miscttf

My problem is that I can't create /usr/share/fonts/miscttf in /usr/share/fonts because under properties I am not the 'owner'.  I've checked in nautilus and I am only owner of files and directories under my user name -- i.e. my documents, nothing else.  How do I change this?

I have a feeling I should know this, but I can't remember.

---

### Post by Patrick793 on 2008-12-24
In your home folder, create a folder named ".fonts", without the quotations, including the period, and put your fonts in there.

---

### Post by taurus on 2008-12-24
```
sudo mkdir /usr/share/fonts/miscttf
```
or

```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2008-12-24
See this link for permissions / ownership

In general you should not change ownership / permissions outside of your home directory.

Use sudo or gksu

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Janeleaper on 2008-12-24
Thanks.

I've created the directory, but it won't let me paste the font into it.  How do I do that?

---

### Post by taurus on 2008-12-24
```
gksudo nautilus
```

---

### Post by Janeleaper on 2008-12-24
Thanks.  Eco-font now installed. Btw, it should use up to 20% less printer ink.

---

