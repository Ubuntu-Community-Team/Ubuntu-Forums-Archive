---
title: "Is there a command that..."
date: 2005-11-15
forum: Desktop Environments
---

### Post by Sunnz on 2005-11-15
Given the name of a directory, scans all text files for a string "foo", and replace it with the string "bar"?

---

### Post by earobinson on 2005-11-15
replaces as in replaces in the out put, or renames as in changes the file names.

But no matter what the answer to your question is yes an no, chances are there is not one command but you will be able to string mutpial commands toghether to do this. Im not on my linux box right now but i suggest looking up.

mv - used to rename
grep - used to replace

these commands may in there man pages point to other commands that will lead you in the right dirction, a string tokeniser is what you are most likley looking for.

and your command will most likley look something like this

ls | grep | mv $1 $2 (it will look a lot different, but the pipeing is correct)
When im next on linux i will give this a go, if you solve it before me then make  a post, and if some one else wants to figure it out go for it.

---

### Post by [2]BoxingFiend on 2005-11-15
there is not really file type extension in unix unlike windows where you use the filename.ext structure.  as a habit i name my files with extensions simply so i can look for them easier.

to change all php files for example [crude bash shell one liner]

ls /path/to/dir/*php; while read fName; do grep "foo" $fName && sed -i 's/foo/bar/g' && echo "changed $fName"; done

psuedo;  list all php extension files in directory, for each file that matches that extension, find the pattern foo in file, then for each file that contains pattern foo replace all foo with bar.

---

### Post by rmjokers on 2005-11-15
Another easy way would be:

perl -pi -e "s/old string/new string/;" /path to directory/*

Basically, you are doing an in-place search-and-replace on the old string in each file given in the list at the end.  See

man perlrun

for details.

---

### Post by earobinson on 2005-11-15
I like the first one better since it is more true to sh!

but the second is cool to, i assume this is using perl lol I dont no perl, The second is probaly more easy for a begginer to use.

---

### Post by az on 2005-11-15
[QUOTE=earobinson] The second is probaly more easy for a begginer to use.[/QUOTE]


This is the first time in history that someone has said that perl is easier for a beginner!

---

### Post by earobinson on 2005-11-15
lol, well the first command is more simple to past in what you need, (its less clunky) and you dont need to learn perl to use it.

perl is a pain to learn, but that line is easy to use without knowing what is going on.

Edit: sp

---

### Post by az on 2005-11-15
[QUOTE=earobinson]perl is a pain to lern[QUOTE]

LOL!  Now *that* is a signature quote! ;)

---

