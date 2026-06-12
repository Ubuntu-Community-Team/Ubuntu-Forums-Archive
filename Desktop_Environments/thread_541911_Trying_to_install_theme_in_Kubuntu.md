---
title: "Trying to install theme in Kubuntu"
date: 2007-09-03
forum: Desktop Environments
---

### Post by Dipper on 2007-09-03
I'm trying to install a theme from kde-look.org.  It's frustrating because they are all source code format and thus can't be installed with the Adept Manager.  The instructions for the particular theme I am trying to install says:

To install: just untar it into ~/.kde/share/apps/deKorator/

I understand that untarring means extracting.  I right-clicked Extract Here and I get a folder with all sorts of icons and graphics (presumably for the theme).  I don't understand the syntax "untar it into ~/.kde/share/apps/deKorator/".  I don't know how I am supposed to do this.

---

### Post by meindian523 on 2007-09-03
Move that extracted folder to /home/your_user_name/.kde/share/apps/deKorator/

Note:To see the .kde folder,you will have to click View menu>>Show hidden files.If one of the folders in the path given above doesn't exist,create it with File>>Create Folder.

---

### Post by meindian523 on 2007-09-03
In linux, ~==your home folder which will be found in /home.

---

### Post by Dipper on 2007-09-03
Thanks for the advice.  There is no deKorator directory in that path.  I used the adept manager to install kwin-style-dekorator, but I don't think I have everything that needs to be installed.

I have searched google and getdeb for a debian version of dekorator.  Unfortunately, all I could find is a tarball and in my experience that means a dead end. Does anyone know of a repository that contains the full dekorator program?

---

### Post by meindian523 on 2007-09-04
> **meindian523 said:**
> If one of the folders in the path given above doesn't exist,create it with File>>Create Folder.

Please do as mentioned above.If the folder doesn't exist,create it!(Ctrl+Shift+N creates a new folder)

---

