---
title: "Change case of file extensions?"
date: 2009-02-19
forum: General Help
---

### Post by kahlil88 on 2009-02-19
Is there a command line program or maybe just a BASH command to change the case of a file extension?

---

### Post by Yellow Pasque on 2009-02-19
Just rename the file with mv, e.g. to change file.txt to file.TXT:
```
mv file.txt file.TXT
```

---

### Post by kahlil88 on 2009-02-20
Oops! I meant to ask how to batch rename. Sorry! :P

---

### Post by Yellow Pasque on 2009-02-20
It depends on where these files are located. Please give more info on what you're trying to do.

---

### Post by kaibob on 2009-02-20
If the files are in one directory, the following will do what you want:

```
rename -n 's/.JPG$/.jpg/' *.JPG
```

This command changes all files with uppercase JPG extensions to lower case. Change .JPG and .jpg to whatever meets your needs. The option, -n, does a dry run and shows proposed changes. Substitute -v for -n to make the actual changes.

If you need to rename the files recursively, let us know, as this is easily done with rename and the find command.

---

### Post by kahlil88 on 2009-03-12
> **kaibob said:**
> If the files are in one directory, the following will do what you want:

```
rename -n 's/.JPG$/.jpg/' *.JPG
```

This command changes all files with uppercase JPG extensions to lower case. Change .JPG and .jpg to whatever meets your needs. The option, -n, does a dry run and shows proposed changes. Substitute -v for -n to make the actual changes.
I tried this, but it didn't work.

---

### Post by kaibob on 2009-03-12
> **kahlil88 said:**
> I tried this, but it didn't work.

I just checked the command line on some test files, and it worked fine. Please explain in a bit more detail what you're doing and what happens.

---

### Post by dpwilson on 2010-12-11
> **kaibob said:**
> 
If you need to rename the files recursively, let us know, as this is easily done with rename and the find command.

Can you tell me how this is done?  I have a lot of .JPG files to change to .jpg and they are of course in many directories.  

For some reason, flash uploader will not list .JPG (uppercase), so I need to convert them to lowercase.

---

### Post by sisco311 on 2010-12-11
Try:
```
find path/to/dir -name "*.JPG" -exec rename -n 's/.JPG/.jpg/' '{}' +
```

---

### Post by nothingspecial on 2010-12-11
Hi sisco :)

explain the + at the end please

cheers

---

### Post by sisco311 on 2010-12-11
Hi,

**-exec command {} \;** runs the command once on each matched file.

command file1
command file2
command file3
...

**-exec command {} +** runs the command on the selected files, but the command line is built by appending each selected file name at the end.

command file1 file2 file3

---

### Post by nothingspecial on 2010-12-11
Thanks. :D

---

### Post by dpwilson on 2010-12-12
Thanks Sisco, worked like a charm

---

### Post by sisco311 on 2010-12-12
> **nothingspecial said:**
> Thanks. :D

> **dpwilson said:**
> Thanks Sisco, worked like a charm

You are welcome!

---

### Post by nothingspecial on 2010-12-12
Sorry......

Can you put this in stupid English?

I realise it is not your first language, even if it is mine.

I am the stupid one......

However, I`ve messed with this for an hour, and fail to see the difference between <+> and <\;> when recursively renaming files.

I do know what the \; does, it`s just that I don`t understand the +

I`m not being rude, I hope, it`s just that whichever way I try I get the same result.

<<confused>> (but would like to understand:D)

---

### Post by AlphaLexman on 2010-12-12
By using the plus sign, sisco311 is renaming the files by calling the 'rename' command only once, which means less work, so your machine does NOT have to execute a command (rename) and exit for every file.

---

### Post by nothingspecial on 2010-12-12
Hang on, I think I got it.

So, with the +, rename will (sort of) treat (the input) as a list.

So rather than starting again for every file, it will read them all, bone after another. In one {job,batch,etc}?

Running once? Rather than an individual instance/process for each file? 

.........


......... And if I don`t "get it", please point me somewhere ------ thanks :D

---

### Post by AlphaLexman on 2010-12-12
It's like this:
```
ls a*.jpg
ls b*.jpg
ls c*.jpg
```
is less efficient than:
```
ls a*.jpg b*.jpg c*.jpg
```
where the /bin/ls program is invoked only once. In reality many mordern machines as well as the user might not even notice the difference.

---

### Post by nothingspecial on 2010-12-12
Thanks :D

So excepting the fact I typed bone instead of one, I get it?

Calling a process once, for a number of files, is more efficient than calling it one time for each file.

Which I know.

I just didn`t understand the +

And I still don`t know how to use it.

So my question remains......

...... a good page on the use of +

Thank you :D

---

### Post by sisco311 on 2010-12-15
> **nothingspecial said:**
> Thanks :D

So excepting the fact I typed bone instead of one, I get it?

Calling a process once, for a number of files, is more efficient than calling it one time for each file.

Which I know.


Yes you understand it correctly.

> **nothingspecial said:**
> However, I`ve messed with this for an hour, and fail to see the difference between <+> and <\;> when recursively renaming files.


You have to rename a lot of files to notice the speed differences:
```
sisco@acme:~$ mkdir ~/test
sisco@acme:~$ touch ~/test/file{1..5000}
time find ~/test -type f -exec touch '{}' \;

real	0m10.984s
user	0m0.207s
sys	0m1.307s
sisco@acme:~$ time find ~/test -type f -exec touch '{}' +

real	0m0.106s
user	0m0.007s
sys	0m0.063s

```

---

### Post by nothingspecial on 2010-12-15
Thanks again :D

---

### Post by kid1000002000 on 2011-01-04
if it didnt work for you try here
[http://ubuntuforums.org/showthread.php?t=1246487](http://ubuntuforums.org/showthread.php?t=1246487)

---

