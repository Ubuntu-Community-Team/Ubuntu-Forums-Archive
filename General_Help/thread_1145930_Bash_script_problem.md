---
title: "Bash script problem"
date: 2009-05-02
forum: General Help
---

### Post by MeKino on 2009-05-02
Hi,

I recently upgraded to jaunty and I don't know if I'm doing something wrong but I can no longer get my shell script to run properly.

I have a folder containing a shell script which records tv to my hard drive.
If I right-click and select RUN everything works fine.

I then went to the terminal and created a link to this script in /usr/bin/ (so I could use crontab to record at specific times)

Executing the script via the link or just typing the name in the terminal produces: bash:command not found

Can anybody tell me what the problem is??

The script clearly works I just can't run it from a link - it's driving me crazy!

Thanks in advance.

---

### Post by mali2297 on 2009-05-02
Check the permissions of the script as well as the link,
```

ls -l /path/to/script /path/to/link

```
Perhaps you need to make one or the other executable.

---

### Post by MeKino on 2009-05-02
Thanks for that, but the script is definitely executable.

I even copied the script to /usr/bin and tried running it directly and still get an error message. I tried running it with the -x option and the reply was 

No such file or directory

yet all I'm doing is saving a file to my home folder - which it does perfectly ok running the script otherwise.

---

### Post by mali2297 on 2009-05-02
Try
```

chmod +x /full/path/to/your/script
/full/path/to/your/script

```

---

### Post by MeKino on 2009-05-02
OK, first I tried

chmod +x /full/path/to/your/script

no problems

then

chmod +x /full/path/to/link

which gave

chmod: cannot operate on dangling symlink

The problem seems to be that a file or folder is not recognised when the script is run via a link (or even directly from /usr/bin/) but runs fine otherwise.

---

### Post by geirha on 2009-05-02
dangling symlink means the symlink isn't pointing to an exisiting file, so you haven't created the symlink correctly ...

---

### Post by disabledaccount01 on 2009-05-02
Message removed by author.

---

### Post by MeKino on 2009-05-02
Thanks - at last!

I had forgotten to include /media/... in the full path.

(Excuse me while I go kick myself).           :lolflag:

---

