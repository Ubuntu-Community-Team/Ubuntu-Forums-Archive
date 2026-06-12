---
title: "file management/permissions"
date: 2005-10-29
forum: Desktop Environments
---

### Post by mcoon on 2005-10-29
I coppied some files from a CD to a desktop folder, and now can't delete them.  the system keeps telling me I don't have permissions to modify its parent folder.

I am a home user, not on a network, and I am the only user. it shows me as the owner of the files on the permissions tab.

any clue how I can fix this?

all the files I've coppied over have little padlocks over the corners.  :(

---

### Post by poptones on 2005-10-29
in the folder, hit ctrl-a to select ALL the files. The right click on one of them and select "properties." Then click "permissions." Click the box that corresponds to your name > write or change.

The files you copied from the CD are write protected because the CD was write protected (ie you annot alter the data on a CD). Give yourself write permissions and the padlocks will go away :)

---

### Post by csaveanu on 2005-10-29
Linux experts do not consider this 'behaviour' (blocking write access to files that come from a read-only media) as a problem but I think there something has to be done to find a better solution. Maybe the system should 'know' if files come from a read-only drive and change permissions automatically. While user permissions are an important security issue, desktop computing looks more or less incompatible with it.

One more thing. Sometimes you cannot change permissions from Nautilus because you're not the "owner" of the files (I think). In that case you have to  go in Terminal and type: sudo chmod -R 777 your_folder_or_file. The -R option is for recursive changes down the folder. 777 is probably not the best thing to do - permissions to read/write/execute for anyone, but is easy to remember.

Cosmin

---

### Post by clearnitesky on 2005-10-29
[QUOTE=csaveanu]One more thing. Sometimes you cannot change permissions from Nautilus because you're not the "owner" of the files (I think). In that case you have to  go in Terminal and type: sudo chmod -R 777 your_folder_or_file. The -R option is for recursive changes down the folder. 777 is probably not the best thing to do - permissions to read/write/execute for anyone, but is easy to remember.[/QUOTE]

Nah, that doesn't change ownership, it changes the permissions. The "chown" command changes owner, for example:

$ sudo chown <your_name>:users <file_name>

"chmod" changes permissions, which dictates what the owner is allowed to do. Don't forget that folders have to be execuable (chmod +x) because otherwise the system will just see them as an ordinary file.

---

### Post by poptones on 2005-10-29
*poptones fires up his laptop running windows 2000 and copies some files from a knoppix cd to "My Documents..."*

Lesseee now, I right click on one of these documents, select properties and.. what does it say?

Sure enough - "read only."

Click "delete" and we get... "Are you sure you want to move the Write Protected document... to the trash bin?"

The foible in Nautilus is that it doesn't ask you to verify you REALLY want to do this - it simply doesn't allow you to do it. I really don't see this as an error, but I do think it would be better if the error message included an EXPLANATION for those who do not know what's going on - a panel that said something like "The file you are trying to delete is in a write protected folder. Are you certain you want to delete this file?" 

Then, if the user says "yes" but it still cannot alter the properties to force a removal, pop up again with something like "this folder is not owned by you, therefore you cannot remove it. You may be able to take ownership of the folder and delete the file by typing your password below..."

---

