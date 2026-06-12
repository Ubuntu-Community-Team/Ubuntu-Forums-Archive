---
title: "download an archive, extract it and save the original file with pipes"
date: 2009-02-12
forum: General Help
---

### Post by googlorenz on 2009-02-12
**[COLOR="Red"]SOLVED![/COLOR]**
Hello,

today I wanted to download a .tar.bz2 file, and decompress it and write the original file to the harddrive in one step

for this i used the following command:
```

screen wget -O - http://someurl.com/somefile.tar.bz2 | tee ./the_original_file.tar.bz2 | tar -xjv --directory=./extract_my_file_here

```
(i used screen since i was connected to the machine via ssh and wanted to be able to close the session)

when i did this i received the following error:

bzip2: Compressed file ends unexpectedly; perhaps it is corrupted? *Possible* reason follows.
bzip2: Invalid Argument
Input file = (stdin), output file = (stdout)

however, the file i am downloading is perfectly alright, and first downloading and then decompressing it works.

what error did i make? (i am running an ubuntu 8.04 amd64 server)

---

### Post by jerome1232 on 2009-02-12
Well I have to say I'm not sure why your tossing tee into there seems like it's not need but this worked fine for me (I used mupen64  because I happened to have it's project page up at the time)

```
jeremy@direbane:~$ wget -O - http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2 | tar xjv -C src/
```

It downloaded mupen64, piped it to tar and extracted it to ~/src/ just fine.


--edit-- actually I think I see what's going on in your command. Your pipeing wget to tee then telling tee to look at a file that doesn't exist because wget is writing the file to standard output not a file.

---

### Post by googlorenz on 2009-02-12
well, i want to download the file, but extract it and keep it at the same time!
basically my command is supposed to work like this:
1. wget downloads the file and writes it to stdout
2. tee reads the file from stdin, and outputs it to the harddrive. at the same time it passes the file on to stdout
3. tar extracts the file.

---

### Post by googlorenz on 2009-02-12
ah: i think i found the problem
the problem is screen!
the screen output is piped into tar.
-> the wget progress bar is no valid compressed file
-> i get an error

so when i run it without screen, everything works fine :)

@jerome
thank you for your help!

---

### Post by jerome1232 on 2009-02-12
Oh okay I get it now (After looking at tee's man page I thought it read from a file to standard output, but it's the opposite). Actually that works just fine as you did it originally for me so I guess I saw an error where there wasn't one. I don't know why it's not working for you sorry.  

```
wget -O - http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2 | tee ./mupen64-0.5.tar.bz2 | tar xjv -C src/

```

That downloaded mupen64, sent it to tee, tee saved the file and piped it right over to tar. Everything extracted just fine.

Sorry I wasn't any help :redface:

---

### Post by googlorenz on 2009-02-12
> **jerome1232 said:**
> Oh okay I get it now (After looking at tee's man page I thought it read from a file to standard output, but it's the opposite). Actually that works just fine as you did it originally for me so I guess I saw an error where there wasn't one. I don't know why it's not working for you sorry.  

```
wget -O - http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2 | tee ./mupen64-0.5.tar.bz2 | tar xjv -C src/

```

That downloaded mupen64, sent it to tee, tee saved the file and piped it right over to tar. Everything extracted just fine.

Sorry I wasn't any help :redface:
actually you were very helpful :)
i tried out your command, saw that it worked, wondered where the substantial differences were, and understood that screen caused my problem.

---

### Post by heindsight on 2009-02-13
Try doing:
```
screen sh -c "wget -O - http://someurl.com/somefile.tar.bz2 | tee ./the_original_file.tar.bz2 | tar -xjv --directory=./extract_my_file_here"
```

---

