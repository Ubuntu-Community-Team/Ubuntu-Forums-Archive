---
title: "Recursive Hardlink?"
date: 2009-04-18
forum: General Help
---

### Post by mythmon on 2009-04-18
So, heres the situation.

My friend and I share a computer. We have a "public" user that holds shared data. What I would like to do is put all of our music together in one folder on this public user, and then hard link what we individually want to our ~/Music folders.

Since we cannot hard link directories, we are creating the directory structure by hand, and then individually hard linking every file.

This works just fine, except we have to individually hard link every single file, and this is annoying. I don't want to copy the files, because that would duplicate space used on the drive, and stop meta data from being shared when we change it.

Also, I found a script that almost did this, but it broke on files with spaces, which was 100% of them. The script was

```
#!/bin/bash
src=$(cd $1 ; pwd)
dst=$(cd $2 ; pwd)

echo "Building new directories in $dest..."
for dir in $(find $src -type d); do
	mkdir -p $dst${dir#$src}
done

echo "Symlinking files..."
for src_f in $(find $src -type f); do
	dst_f=$dst${src_f#$src}
	ln $src_f $dst_f
done

echo "Success"
```

So does anyone know of a way to hard link every file in a directory recursively? Or does anyone know what causes the above script to do funny things with spaces in the file name?

---

### Post by cariboo on 2009-04-18
The way I would solve the problem, is to create a directory in /home eg:

```
/home/music
```

and make the directory world read/writeable, then you can create a sym-link in your home directory to wherever you want, and your buddy can do the same in his home directory eg:

```
sudo ln -s /home/music /home/<user>/tunes
```

Jim

---

### Post by mythmon on 2009-04-18
Jim: That would solve the problem of the duplication of used space, but the thing is, we don't want the three directories to be required to have the same contents.

So if the shared folder holds music (A B C D) then maybe I want (A B C) and he wants (B C D).

We could just soft link that artists/albums/songs we want, but I think that in this situation a hard link is what I want.

-Mike

---

### Post by dcstar on 2009-04-18
> **mythmon said:**
> 
........
So does anyone know of a way to hard link every file in a directory recursively? Or does anyone know what causes the above script to do funny things with spaces in the file name?

Surround all file name variables with " " or ' ' characters.

---

### Post by mythmon on 2009-04-19
> **dcstar said:**
> Surround all file name variables with " " or ' ' characters.

I tried that. The line in the script that reads
```
for dir in $(find "$src" -type d); do
```
loops over every word in each file name, since the loop splits it apart on the spaces anyways. I haven't been able to figure out how to make it do other wise yet, but I have been fiddling.

It occurred to me that the loop isn't really necessary, and everything could be done with find. However this brings about another problem, in that the magic that fixes the paths (which is "$dst/${dir#$src}" )  doesn't like find's {} syntax for the found file name.

Is there another way to do this nifty string replacement in bash? Or does someone know sed? (I don't) Or can you change what find replaces with the filename? (something besides {})

Thanks

---

### Post by silvavlis on 2009-05-07
"cp -R -l" would do it :guitar:

---

