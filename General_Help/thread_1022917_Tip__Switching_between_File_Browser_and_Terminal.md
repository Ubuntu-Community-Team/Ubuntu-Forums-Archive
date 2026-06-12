---
title: "Tip : Switching between File Browser and Terminal"
date: 2008-12-27
forum: General Help
---

### Post by qns8dn3 on 2008-12-27
Working in File Browser is easy : deleting, renaming, moving, opening a file, compressing a folder, they are all done easily using mouse clicks.

Working in Terminal requires learning things such as cd, mv, rm, cp, tar, bash but you can do more things in terminal : such as deleting all files that ends with ".log" and shell scripting.

Let's take advantage of both. Here is how to quickly switch between the two.

To switching from File Browser to Terminal, right click on an empty area in File Browser window, click on "Open in Terminal" item in the popping menu. Terminal window will appear and its current directory is the same as that in the File Browser. Alternatively, it's also in menu : File > Open in Terminal. If you don't see 'Open in Terminal' item, install nautilus-open-terminal package.

To switch from Terminal to File Browser, Enter the following command (including the dot):
    ```
nautilus .
```
File Browser will open your current directory.
  
I switch to Terminal when I need shell globbing feature and switch to File Browser when I need to preview image files quickly.

This tip applies to Ubuntu. Anybody want to post Kubuntu version and Xubuntu version?

If you often find yourself switching from Terminal to File Browser just to remove files in a way that can be restored from Trash, or just to open a file, you should look into trash-cli package and xdg-open command.

---

