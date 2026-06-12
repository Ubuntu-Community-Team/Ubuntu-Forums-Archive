---
title: "problem to rename a file"
date: 2009-04-19
forum: General Help
---

### Post by Cecilio on 2009-04-19
I'm having a problem to rename a file.

I have a dual boot system (Windows XP & Ubuntu). I have a file in the windows NTFS volume. I created this file with name  'authors' and now I'm trying to rename it as 'AUTHORS'.

From Windows I reamed it as 'authors2' and then as 'AUTHORS'. Windows reports now its name as 'AUTHORS' (from Explorer). Also from a command window, the 'dir' command reports its name as 'AUTHORS'.

But from Ubuntu, the name continues being reported as 'authors'. So, from Ubuntu I did:

    mv authors AUTHORS

And get error:

    mv: «authors» y «AUTHORS» are the same file

So I did:

    mv authors AUTHORSX
    ls

and I get:
    
    authorsx

(note that name 'authorsx' never existed previously in that floder) so I think this is not Windows fault. But if I do:

    mv authorsx AUTHORS.txt
    ls

I get

    AUTHORS.txt

If now I do:

    mv AUTHORS.txt AUTHORS
    ls

I get:

    authors

So, the problem seems to be associated to files with all chars in uppercase letters.

I'm too new to Linux to think about how to solve this, and I'm becoming crazy!!! Please help!!!!

---

