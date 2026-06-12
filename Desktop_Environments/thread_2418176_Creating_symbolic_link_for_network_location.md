---
title: "Creating symbolic link for network location?"
date: 2019-05-02
forum: Desktop Environments
---

### Post by nikt3 on 2019-05-02
Hello

When I am creating a symbolic link for some of my network location I get the error message that: "could not create symbolic link to ... because it's not local file".
Would it be possible to somehow overcome this problem?

Xubuntu 18.10, Thunar.

---

### Post by Dennis N on 2019-05-02
I make bookmarks to specific folders on the server that contains my data. That works well for me.

---

### Post by nikt3 on 2019-05-03
> **Dennis N said:**
> ...
@Dennis N, could you explain the steps please? I can not find this function in my system.

---

### Post by Holger_Gehrke on 2019-05-03
The sidebar has two modes: tree and places / bookmarks. You can switch between the two modes in the "View"-menu or by hitting ctrl-b (bookmark) or ctrl-e (tree). If the sidebar is in bookmark mode, you can just drag and drop directories from the main-panel into the sidebar to create a new bookmark. You can also select "send to->Sidebar(create new Bookmark)" from the context menu of a directory.

Also: while "Edit->Create Link"  doesn't work for files on network locations, you can also create symbolic links to files or directories by drag and drop. Start the drag normally then hold **ctrl and shift** during drop to create a link. On XUbuntu 18.04 I'm able to create symbolic links in my home directory to files on a samba share in this way, either by dropping into the sidebar or into a second Thunar window.

Holger

---

### Post by Dennis N on 2019-05-03
> **nikt3 said:**
> @Dennis N, could you explain the steps please? I can not find this function in my system.

I used gigolo* to establish the initial connection since I like GUIs that make things easy. Then open the remote location from gigolo's window - it opens in Thunar. Browse arould and set Thunar bookmarks for the folders you want to access. 

After bookmarks are made, you don't need to remember the details of connection. You don't even need gigolo. Clicking on a bookmark in Thunar (or Files if done with Ubuntu) will do the connect and open Thunar window at the remote location. A popup dialog will initially ask for password, but there is a box to remember the password so you don't have to enter one in the future.

My personal server is on my LAN, so that is the extent of my use. 

*I think gigolo was in the default Xubuntu install, but you can install it from the repositories. It can manage multiple connections simultaneously, and remembers all the details of the connecting.

---

