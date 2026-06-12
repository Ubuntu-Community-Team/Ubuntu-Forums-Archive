---
title: "How do I do a search, for example all photos with the word kitchen in it and then cop"
date: 2009-01-18
forum: General Help
---

### Post by Rytron on 2009-01-18
Hi.
How do I do a search, for example all photos with the word kitchen in it and then copy those photos into a folder?

I know how to use the wild card *kitchen*. But I want to know how to copy all these photos to a folder on my desktop named kitchen photos.

Thanks.

---

### Post by SPr on 2009-01-18
```

for i in $(ls -R *kitchen*); do cp ${i} ~/Desktop/kitchen\ photos/;done

```
ls -R is recursive so depending on the search folder structure using a plain ls could work.

---

### Post by heindsight on 2009-01-18
> **SPr said:**
> ```

for i in $(ls -R *kitchen*); do cp ${i} ~/Desktop/kitchen\ photos/;done

```


I'm not sure that will work. If all your photos are jpg's stored under the Pictures subdirectory of your home dir, you can do:
```
find ~/Pictures -type f -iname "*kitchen*.jpg" -exec cp "\{\}" ~/Desktop/kitchen\ photos/ \;
```

---

### Post by SPr on 2009-01-18
It worked for me when I tested it :)

---

### Post by heindsight on 2009-01-18
> **SPr said:**
> It worked for me when I tested it :)

yes it can work - but it would copy all the contents of any directory with kitchen in the name too. for a job like this find is just a better tool than ls

---

### Post by MaxIBoy on 2009-01-18
I didn't know ls could take regular expressions like that. I would've done something like "for file in $(ls -R | grep .*kitchen.*jpg);"

---

### Post by Rytron on 2009-01-18
I keep all my pictures here:

```
/home/user/Documents/Pictures_Linux
```

So what will be the full line I need?

---

### Post by heindsight on 2009-01-18
> **Rytron said:**
> I keep all my pictures here:

```
/home/user/Documents/Pictures_Linux
```

So what will be the full line I need?

```
find /home/user/Documents/Pictures_Linux -type f -iname "*kitchen*.jpg" -exec cp "\{\}" ~/Desktop/kitchen\ photos/ \;
```

this will find all files under /home/user/Documents/Pictures_Linux with names containing kitchen and ending in .jpg and copy them to the 'kitchen photos' directory on your desktop (you will have to create the 'kitchen photos' directory first)

---

### Post by Rytron on 2009-01-18
> **heindsight said:**
> ```
find /home/user/Documents/Pictures_Linux -type f -iname "*kitchen*.jpg" -exec cp "\{\}" ~/Desktop/kitchen\ photos/ \;
```

this will find all files under /home/user/Documents/Pictures_Linux with names containing kitchen and ending in .jpg and copy them to the 'kitchen photos' directory on your desktop (you will have to create the 'kitchen photos' directory first)

Output:

```
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
cp: cannot stat `\\{\\}': No such file or directory
```

I created the required folder on my desktop(picture).

---

### Post by heindsight on 2009-01-18
Sorry, i shouldn't have backslash-escaped and quoted those braces.

```
find /home/user/Documents/Pictures_Linux -type f -iname "*kitchen*.jpg" -exec cp \{\} ~/Desktop/kitchen\ photos/ \;
```

should work.

---

### Post by Rytron on 2009-01-18
Thank you so much heindsight. You are a genius. The Ubuntu community is glad to have people like you.

Just one question, is this line case sensitive?

---

### Post by heindsight on 2009-01-19
> **Rytron said:**
> Thank you so much heindsight. You are a genius. The Ubuntu community is glad to have people like you.

Just one question, is this line case sensitive?

A genius I am not, I just have a bit of experience with this sort of thing.

The 'i' in the -iname option to find causes find to search case insensitively. So this will find files with kitchen as well as Kitchen or KiTchEN etc. If you want a case sensitive search, just replace the -iname with -name

---

### Post by Rytron on 2009-01-19
Cheers to you heindsight. It is very useful to be able to quickly copy files that meet certain criteria.

---

### Post by Rytron on 2009-01-19
Windows XP has the function of right clicking on search results and copying and pasting them anywhere. Ubuntu 
should have this feature as standard. Is there talk of this feature being added to Ubuntu 9.04 / 9.10?

---

