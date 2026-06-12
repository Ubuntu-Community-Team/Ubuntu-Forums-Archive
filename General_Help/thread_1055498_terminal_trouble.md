---
title: "terminal trouble"
date: 2009-01-30
forum: General Help
---

### Post by cyberpirate on 2009-01-30
im having trouble with my terminal when i give it certain commands like 

```

sudo mount -t ntfs-3g /dev/sdb1 /mount/disk

```

or

```

sudo cp /myfile /destination

```

im giving the copy command root access cuz im trying to backup a root protected file

but all i get for my effort when i press enter is this

>

i press enter again and it does the same thing and if i pres crl + c then it takes me back to the menu. i have hardy heron and i already checked for updates. any ideas as to whats going on here?

---

### Post by taurus on 2009-01-30
Can you post a screenshot of that, Applications -> Accessories -> Take Screenshot?

---

### Post by cdtech on 2009-01-30
Try running the "mount" command without the -t flag:
```
sudo mount /dev/sdb1 /mount/disk
```
The newer kernel images are now implemented with the NTFS. It should auto detect. Let me know what the output is.......

---

### Post by cyberpirate on 2009-01-30
i got the mount to work. i booted up window xp and dismounted it correctly
its the file i really want to back up

i cant post an image for some reason its just this anyway

```

sudo cd KEY /mount/drive
>

```

---

### Post by snova on 2009-01-30
What, precisely, is the name of the mountpoint? I'm guessing there's an apostrophe or something in the name.

---

### Post by cyberpirate on 2009-01-30
yes in both commands i was working with a drive that had an apostrophe in the name

---

### Post by snova on 2009-01-30
It's waiting for the other one.

Escape the quote with a backslash, like so:

```
sudo mount -t ntfs-3g /dev/device /media/The\'Name
```

Or with the other type of quote:

```
sudo mount -t ntfs-3g /dev/device "/media/The'Name"
```

---

### Post by cyberpirate on 2009-01-30
yay that worked! thx!

---

### Post by hl2040 on 2009-01-30
> **cyberpirate said:**
> im having trouble with my terminal when i give it certain commands like 

```

sudo mount -t ntfs-3g /dev/sdb1 /mount/disk

```

or

```

sudo cp /myfile /destination

```

im giving the copy command root access cuz im trying to backup a root protected file

but all i get for my effort when i press enter is this

>

i press enter again and it does the same thing and if i pres crl + c then it takes me back to the menu. i have hardy heron and i already checked for updates. any ideas as to whats going on here?

It looks like there is something wrong with your shell. I usually see that when I am using bash and forget to close a quotation, such as
$ cd "asdf
will result in a ">" prompt on a new line, whereas
$ cd "asdf"
the command will actually get to execute, and actually cd to directory asdf if it exists, and print a message if it does not. The > prompt is bash's way of saying "need further input"

As to *why* this is happening, you might have a messed up ~/.bashrc or some other bash related file. As a dumb fix, try installing another shell such as zsh and see if the problem persists.

---

### Post by slakkie on 2009-01-30
> **hl2040 said:**
> It looks like there is something wrong with your shell. I usually see that when I am using bash and forget to close a quotation, such as
$ cd "asdf
will result in a ">" prompt on a new line, whereas
$ cd "asdf"
the command will actually get to execute, and actually cd to directory asdf if it exists, and print a message if it does not. The > prompt is bash's way of saying "need further input"

As to *why* this is happening, you might have a messed up ~/.bashrc or some other bash related file. As a dumb fix, try installing another shell such as zsh and see if the problem persists.There is nothing wrong with his shell, he forgot to escape the ' or " in the mount point name.

---

### Post by cyberpirate on 2009-01-31
thats what it was... i had an apostrophe and when i put quotes around the drive location it worked. what does the apostrophe mean in the terminal anyway?

---

### Post by cdtech on 2009-01-31
> Full quoting [single quote]. 'STRING' preserves all special characters within STRING. This is a stronger form of quoting than "STRING".
By not closing the quotes (single), your prompted with the charactor ">" for a completion to your command line.

---

### Post by cyberpirate on 2009-01-31
so if i were to have a drive named

/media/'whatever

then i could complete the command with 

>'

and press enter? would it execute even tho it wouldn't execute how i wanted it to?

---

### Post by cdtech on 2009-01-31
Not if it's part of the drive name (ie../my'drivename) then you would need the quote characters:
> Quoting means just that, bracketing a string in quotes. This has the effect of protecting special characters in the string from reinterpretation or expansion by the shell or shell script. (A character is "special" if it has an interpretation other than its literal meaning.
Such as:
/"my'drivename"

---

### Post by slakkie on 2009-01-31
> **cyberpirate said:**
> so if i were to have a drive named

/media/'whatever

then i could complete the command with 

>'

and press enter? would it execute even tho it wouldn't execute how i wanted it to?

No, because then you actually are refering to:

/media/'whatever' which is the same as /media/whatever

If you have those single quotes in a name you can escape them or you use quotation: eg /media/\'whatever or /media/"'whatever" or in quote everything "/media/'whatever"

---

