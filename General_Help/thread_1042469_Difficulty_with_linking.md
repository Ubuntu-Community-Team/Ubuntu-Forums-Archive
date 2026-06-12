---
title: "Difficulty with linking"
date: 2009-01-17
forum: General Help
---

### Post by Daminvar on 2009-01-17
I want to make a link to a file so that rather than typing '/dir/blah/blah/blah.sh args' I can type './blah.sh args'.  I managed to link to the file just fine, but when I try to run the script, it fails because it depends on other files in its directory.  Is there a way to make a link that will not have that problem?

Thanks in advance. :)

~Daminvar

---

### Post by ajcham on 2009-01-17
I'm not sure if it's possible - you may have to create links to the other files also (assuming there aren't too many), but I'm not sure.

As an alternative, you could set an alias for the command to run the script.
```
alias blah='/dir/blah/blah/blah.sh'
```
You would have to add the alias command to your ~/.bashrc (assuming you use bash) to avoid having to type it every time you launch a new shell.

---

### Post by cdtech on 2009-01-17
Create an alias to do the job for you:
```
pico ~/.bash_aliases
```
Or if your still using .bashrc:
```
pico ~/.bashrc
```
**UPDATE::.**
You could also create functions within your .bash_aliases file such as:
```

# functions
################################################## #########
function mkdcd ()
{
    if [ $# -ne 1 ]; then
        echo 'function takes exactly one argument!'
        return 1
    fi
    mkdir "$1"
    cd "$1"
}

```

---

### Post by Daminvar on 2009-01-17
Using an alias worked out great.  Now I don't have to type nearly as much.

Thank you both. =)

~Daminvar

---

