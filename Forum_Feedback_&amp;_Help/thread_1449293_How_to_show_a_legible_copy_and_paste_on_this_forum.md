---
title: "How to show a legible copy and paste on this forum"
date: 2010-04-07
forum: Forum Feedback &amp; Help
---

### Post by ricyaun on 2010-04-07
Thought I might try a new question.  How to put a legible copy and paste on ubuntu forums or upload a a screenshot to the forum as part of a question.

Thanks for any help I can get.
ricyaun

---

### Post by spiky001 on 2010-04-07
I take a screen shot save it to pics as jpeg,  Then open reply click the paper clip attachment then browse to folder get pic upload it should work  use the upload button at bottem of the 4 browse buttons

---

### Post by sisco311 on 2010-04-07
Check out the *Guide to Forum features* link from my signature.

---

### Post by ricyaun on 2010-04-07
> **spiky001 said:**
> I take a screen shot save it to pics as jpeg,  Then open reply click the paper clip attachment then browse to folder get pic upload it should work  use the upload button at bottem of the 4 browse buttons

Thanks but doesn't really make a legible picture.  What is gosalia?

ricyaun

---

### Post by srs5694 on 2010-04-07
The screen shot shown when you view the thread is shrunk. When you click it, it's shown full size and is much more legible.

For text-only information, especially information from a console display that includes columns, indents, etc. (for instance, the output of "sudo fdisk -l"), use code blocks. These begin with the word "code" inside square braces and end with "/code" in square braces. It looks something like this:

[ code ]
Cut-and-pasted text
[ /code ]

You must close up the spaces within the square braces.

As an example of this technique and how it improves legibility, consider the following cut-and-pasted text, outside and then inside a code block:

$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.6.6

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): B322E151-7686-4B94-ACDF-F8F4CC2E9813
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 1-sector boundaries
Total free space is 4670 sectors (2.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          390625   190.7 MiB   0700  Unused
   2          390626          803249   201.5 MiB   0700  Gentoo /boot
   3          803250         1212850   200.0 MiB   0700  Ubuntu /boot
   4         1212851       976768064   465.2 GiB   8E00  Linux LVM data (nessus)
   5       976768065       976768464   200.0 KiB   EF02  BIOS boot partition

The columns don't line up, making it much harder to interpret than when it's done inside a code block:

```

$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.6.6

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): B322E151-7686-4B94-ACDF-F8F4CC2E9813
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 1-sector boundaries
Total free space is 4670 sectors (2.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          390625   190.7 MiB   0700  Unused
   2          390626          803249   201.5 MiB   0700  Gentoo /boot
   3          803250         1212850   200.0 MiB   0700  Ubuntu /boot
   4         1212851       976768064   465.2 GiB   8E00  Linux LVM data (nessus)
   5       976768065       976768464   200.0 KiB   EF02  BIOS boot partition

```

Much better, yes? Note that, at least on my browser (Firefox in Linux), the font in the reply box is proportional, so the columns don't quite line up for me as I'm typing this, but they should be properly aligned in the final post.

---

### Post by sisco311 on 2010-04-07
> **srs5694 said:**
> These begin with the word "code" inside square braces and end with "/code" in square braces. It looks something like this:

[ code ]
Cut-and-pasted text
[ /code ]

You must close up the spaces within the square braces.



You can use the noparse tags  to stop the parsing of BB code:

[noparse][noparse]**sisco311 is narcistic**[/noparse][/noparse]

[noparse]```
echo Hurray!!!
```[/noparse]

---

