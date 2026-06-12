---
title: "Mass rename of .bmp files"
date: 2009-04-01
forum: General Help
---

### Post by Phalangees on 2009-04-01
Hello Everyone,

Happy April Fools day. I love the website. ;)

I have a quick question. I'm not very good at shell commands so I was hoping someone could help me out. I have album art for my albums in the album folder named cover.240x240.bmp and I need to rename it to cover.bmp. The thing is, I have hundreds of albums so doing it individually would be incredibly time consuming.

This is what my directory setup is like:

+Music
-+Artist Name
--+Album 1
---+Music File 1
---+Music File 2
---+cover.240x240.bmp
--+Album 2
---+Music File 1
---+Music File 2
-+Artist 2
--+Album 1
...etc. Hopefully you get the idea.

If anyone knows a shell command to do this please let me know.

Thank you all so much!!

---

### Post by kaibob on 2009-04-01
The following should do what you want. You will have to modify the path.

```
find /home/username/music -name 'cover.240x240.bmp' -type d -exec rename -n 's/cover.240x240.bmp/cover.bmp/' '{}' ';'
```

The -n option directs rename to do a dry run and report proposed changes. Substitute -v for -n to actually rename the directories. I checked this command but you should still have a backup.

BTW, the title of this thread is " Mass rename of .bmp files" but the post seems to indicate that you want to rename folders. My command assumes the latter.

---

### Post by Phalangees on 2009-04-01
Thanks a lot for the command but I'm actually looking to change .bmp files. The folders that the files are contained in is the album folder so the cover.240x240.bmp is the picture of the album art. I just need to change it to cover.bmp.

I need the folder structure to stay the same.

Thanks again for your help. I appreciate it.

---

### Post by kaibob on 2009-04-02
Phalangees,

I've been working most of the day to resolve a number of computer problems and my brain isn't working well at the moment. If you want to rename all files located in the music directory and subdirectories from cover.240x240.bmp to cover.bmp, you only need to change -type d in my original command to -type f. So, the new command would be:

```
find /home/username/music -name 'cover.240x240.bmp' -type f -exec rename -n 's/cover.240x240.bmp/cover.bmp/' '{}' ';'
```

As before, change the path to the music folder as needed. This command does not change the directory structure or location of the renamed files but use the -n option to check things and have a backup just in case. 

If I still don't understand your request correctly, perhaps someone else can help. Renaming files like this is pretty straightforward stuff once you learn the basic commands. 

kaibob

---

