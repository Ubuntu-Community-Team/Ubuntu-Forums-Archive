---
title: "random in find and readdir()"
date: 2009-08-11
forum: Desktop Environments
---

### Post by morio.kalani on 2009-08-11
hi...

I noticed something a while ago, like you see in my signature i like to play my music with mplayer through find on the commandline...

The only problem it gives, it randomizes all the files, instead of playing them from 1 to 10...
I didn't mind, till now, cause i started to write some c# code...

I'm using readdir and it works! But it only scrambles the output and gives the first entry a second time at the end...

I made it short and compilable without my whole program...
If someone can help me with this problem, i would appreciate it very much...   
Is it due the random of Ubuntu (Like the find command???) or do i have to change code...

```
#include <stdio.h>
#include <errno.h>
#include <sys/types.h>
#include <dirent.h>  

#define dir getenv("HOME")

main()
{
DIR *dip;
struct dirent *dit;

 dip = opendir(dir);
  if (dip == NULL)
    {
      perror("opendir");
      return(CODE);
      } 
      while ((dit = readdir(dip)) != NULL)
    {
      printf("\n%s",dit->d_name);
    }
  closedir(dip);
}
```

---

