---
title: "Help with getlive"
date: 2009-03-15
forum: General Help
---

### Post by marcus_mercado on 2009-03-15
I am stuck with my getliverc file. My current rcfile is

```
mode=200902
username=user
password=pass
domain=hotmail.com
MoveToFolder=/home/user/Documents
Folder=Inbox
#Downloaded=/home/user/.getlive.log
#delete=Yes
FetchOnlyUnread=Yes
RetryLimit=3
```

What gives me the error is the line
 ```
"MoveToFolder=/home/user/Documents". 
```

I get the error

```
GetLive died with message: 'Folder with name '/home/user/Documents' used in MoveToFolder could not be located. at /usr/bin/getlive line 802.
```

When I comment the line '/home/user/Documents' off, the program works perfect. However I dont know where my fetched mail goes :(

The man page describes MoveToFolder as

```
       MoveToFolder
              Folder  to  which  the  message  must be moved after being down&#8208;
              loaded.  If this argument takes  the  form  @FileName  then  the
              folder name is taken from the contents of the file.

              This can be used, for example, to enable a spam filter to decide
              to what folder the message must be moved. That spamfilter  would
              be  invoked by the Processor option and then write a folder name
              (for instance Junk if considered junk) to the file FileName.

              Note that a message is not moved if it’s not downloaded  due  to
              it being already in the Downloaded file.

```

Can anyone help and tell me what I'm doing wrong?

---

### Post by marcus_mercado on 2009-03-16
bump*

---

