---
title: "Reach my server files?"
date: 2008-12-27
forum: General Help
---

### Post by Emmas on 2008-12-27
Hello, I have a big problem. 
I want to be able to reach my multimedia files from my Windows home server (2003). I recently installed Ubuntu on my laptop but now I can't reach my movies and so on... I wondering if there is some kind of program or likely that will solve my problem.

Plz help :)

---

### Post by damis648 on 2008-12-27
How are the files being shared? FTP? SMB Shares?

---

### Post by Emmas on 2008-12-27
> **damis648 said:**
> How are the files being shared? FTP? SMB Shares?

I´m using just shared folders on windows home server like a small network, the shared folders are in NTFS format.

---

### Post by damis648 on 2008-12-27
Ah, ok. Open a terminal (Applications>Accessories>Terminal) and enter
```
sudo apt-get install samba
```
and enter. Once that is done, go to Places>Network>Windows Network. You will find it there. Cheers! :popcorn:

---

### Post by namdung on 2008-12-27
I reckon that the files are in ur Windows PC and u want to access them via ur Ubuntu PC. I'm also assuming ur PCs are connected and able to ping each other.

Press ```
Alt+F2
``` 
Type: ```
smb://win_pc/sharename
```

Where *win_pc* is the IP or the hostname of the Windows PC and *sharename* is the name share folder

---

### Post by Emmas on 2008-12-27
> **damis648 said:**
> Ah, ok. Open a terminal (Applications>Accessories>Terminal) and enter
sudo apt-get install samba
and enter. Once that is done, go to Places>Network>Windows Network. You will find it there. Cheers! :popcorn:

Sorry but it didn't work :( 
I can reach the server but the contents isn't there...

---

### Post by damis648 on 2008-12-27
> **namdung said:**
> I reckon that the files are in ur Windows PC and u want to access them via ur Ubuntu PC. I'm also assuming ur PCs are connected and able to ping each other.

Press ```
Alt+F2
``` 
Type: ```
smb://win_pc/sharename
```

Where *win_pc* is the IP or the hostname of the Windows PC and *sharename* is the name share folder

The IP wouldn't work, that's a different protocol. In any case, you can just use Places>Network.

EDIT: Just saw your reply. Maybe it is password protected, or you need a username? Try Places>Connect to Server and then choose 'Windows Share' and fill in the info. As server, put the hostname of the server. (NOT IP)

---

### Post by Emmas on 2008-12-27
> **namdung said:**
> I reckon that the files are in ur Windows PC and u want to access them via ur Ubuntu PC. I'm also assuming ur PCs are connected and able to ping each other.

Press ```
Alt+F2
``` 
Type: ```
smb://win_pc/sharename
```

Where *win_pc* is the IP or the hostname of the Windows PC and *sharename* is the name share folder

I did what you said but it says "Unable to mount windows shared" :S

---

### Post by Emmas on 2008-12-27
> **damis648 said:**
> The IP wouldn't work, that's a different protocol. In any case, you can just use Places>Network.

EDIT: Just saw your reply. Maybe it is password protected, or you need a username? Try Places>Connect to Server and then choose 'Windows Share' and fill in the info. As server, put the hostname of the server. (NOT IP)

It says the same "Unable to mount windows shared" :S

---

