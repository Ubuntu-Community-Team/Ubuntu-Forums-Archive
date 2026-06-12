---
title: "chown resulted in weird permissions, inaccessible files"
date: 2009-03-04
forum: General Help
---

### Post by brouhaha on 2009-03-04
Hi,

First the problem at hand:
* I have no user groups on my laptop.
* There are two users - namit, who is the root; nidhi, who is a non-root user.
* I logged in as namit, and did the following:
```

]$> cd /home/nidhi/Documents
]$> sudo chown nidhi:namit *

```
I realised I did a mistake, but the damage was done. Even after I issued
```

]$> sudo chown nidhi:nidhi *

```
it didn't make any difference.

Please refer to the attached picture for "damage" I'm talking about. 
* I can't see any files if I click on any sub-directories under Documents.
* I can go to the folder in a Terminal and see the files if execute "ls -l", but with weird permissions.
* Nonetheless, I can't open any of the files from either logins.

Secondly, I think it shouldn't have happened in the first place:
* I tried in another machine with Fedora Core installed and gave a similar command "chown <user_id1>:<user_id2> <file_name>" and it gave an error saying that it can't be done.

Please help me out.

Thanks a lot,
Namit

---

### Post by heindsight on 2009-03-04
The problem is not with the ownership but with the permissions.

For everything to work as expected you need both read and execute permissions on a directory. It seems at some point you removed execute permissions from the subdirectories in Documents.

Try doing:
```
chmod a+x /home/nidhi/Documents/{"From office laptop","GoSports Foundation"}
```
to give everyone execute permission, OR
```
chmod ug+x /home/nidhi/Documents/{"From office laptop","GoSports Foundation"}
```
to only give the owner and group execute permission.

You may want to read this: [uhelp]community/FilePermissions[/uhelp]

EDIT:
By the way, if you want to post output from running some command in a terminal, it's better to copy the text and paste it in your post (surrounded by [CODE] tags). It makes it a lot easier to help you, because people can see what's going on without first having to open an attached image.

---

### Post by brouhaha on 2009-03-05
Thanks a lot, heindsight, for your reply.

I'll note the suggestion you gave regarding command outputs. The reason I attached a picture was to show that I could see the files with 'ls' command, but (in the background) no files are visible using folder browser. In fact, at the bottom right of the browser you'll see that it says "0 files", which is strange.

I'll follow your suggestions and let you know whether or not it worked.

---

### Post by brouhaha on 2009-03-05
Success! Thank you very much.

---

