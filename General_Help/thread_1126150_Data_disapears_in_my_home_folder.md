---
title: "Data disapears in my home folder"
date: 2009-04-15
forum: General Help
---

### Post by jon_i_luttra on 2009-04-15
Hello
I have problems with data losses in Ubuntu 8.04 64 bit, it appears like whole days of work just disappears. First I thought that I just had forgot to save or saved the files I was working on in some other folder, but that is not the case. If I do $ls -l for the /home folder no files has been changed the day data has disappeared it is like the computer was newer turned on that day. Is it the hard drive that is corrupt or can something else cause this behavior? I have newer seen something like this in a linux system before.

I'm thankful for any advice that can solve this problem.

/Jon

---

### Post by Peter09 on 2009-04-15
Just to check, you command is actually

```
ls -l /home/<your user name>
```

also what does

```
ls -l ~
```
show

---

### Post by jon_i_luttra on 2009-04-15
> **Peter09 said:**
> Just to check, you command is actually

```
ls -l /home/<your user name>
```

also what does

```
ls -l ~
```
show

Yes and no I did ls -l in the folder where I keep my lost documents and all the files there were last changed two days before the day I did that - one day of changes was lost. Then find was used to see if the document was  accidentaly saved in another folder but it wasn't. Then I checked the whole /home/jon/ folder for changes that day but no files had been changed that day. I think I used the built in GUI for find to do that job and searched for any file that had been accessed that day but no file showed up. I think that is strange since some files should have been altered when writing in documents, receiving emails etc. 

Maybe I should clarify that it is changes done to files that disappear for example I have a article I'm writing in tex, the file is still there but whole days of work can disappear from one day to another. Both the source file and the compiled file seem to have been recreated to a previous state. 

/Jon

---

