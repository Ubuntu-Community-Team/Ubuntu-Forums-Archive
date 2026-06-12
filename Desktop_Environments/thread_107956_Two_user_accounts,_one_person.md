---
title: "Two user accounts, one person"
date: 2005-12-24
forum: Desktop Environments
---

### Post by superkalv on 2005-12-24
I work from home using a single computer for both my work stuff and general private rubbish. I want to set up two accounts for myself to use at the same time: one for work and one for private stuff. My current single home directory contains a large number of existing files that I want to split into two groups. The holiday period is a good opportunity to get organised :)

Anyone else have experience with this?

I know I can set up two accounts, log in to one and then start a new session with 'New Login'. I can then switch between the two with ctrl+alt+f7/f8. That works well :) With time I'll have separate bookmarks, inboxes, etc. I'll get a clear separation of work and home, but I'll be able to flip between the two to check email or whatever.

I'm having problems with file permissions though. I'd like to be able to move files freely between the two home directories with nautilus while logged in to either account (without sudoing). I've set up a group that both users are subscribed to and I've made the home directories writeable to groups (drwxrwxr-x) as well as giving -rw-rw-r-- permissions and relevant group ownership to some files. It sort of works, but I can't move those files from the home dir to the Desktop for some reason and the files are not created with suitable permissions/ownerships by default.

There are clearly some things relating to groups and permissions that I haven't quite got worked out ...

---

### Post by ubuntu27 on 2005-12-24
With this trick, you can open a file or folder/directory as a Root just using Right click and choosing "open as root" [then it ask for your password]. As a root, you will be able to move things around. The great thing about this script is that it lets you be Root in a the directory or files you decided :)

Follow the guide:

[http://ubuntuguide.org/#openfilesasrootviarightclick](http://ubuntuguide.org/#openfilesasrootviarightclick)

---

