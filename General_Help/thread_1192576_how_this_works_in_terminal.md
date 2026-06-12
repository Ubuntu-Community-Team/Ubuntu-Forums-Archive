---
title: "how this works in terminal??"
date: 2009-06-20
forum: General Help
---

### Post by abhilashm86 on 2009-06-20
this is a function i found while customizing .bashrc, this i found in .bashrc
```
function extract()      # Handy Extract Program.
{
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xvjf $1     ;;
             *.tar.gz)    tar xvzf $1     ;;
             *.bz2)       bunzip2 $1      ;;
             *.rar)       unrar x $1      ;;
             *.gz)        gunzip $1       ;;
             *.tar)       tar xvf $1      ;;
             *.tbz2)      tar xvjf $1     ;;
             *.tgz)       tar xvzf $1     ;;
             *.zip)       unzip $1        ;;
             *.Z)         uncompress $1   ;;
             *.7z)        7z x $1         ;;
             *)           echo "'$1' cannot be extracted via >extract<" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

```
so how exactly these extract program works, how to invoke them or do they identify automatically??

---

### Post by mali2297 on 2009-06-20
> **abhilashm86 said:**
> 
so how exactly these extract program works, how to invoke them or do they identify automatically??

Yes. The function chooses command based on the file extension. Invoke it with, for example,
```

extract something.tar.gz

```

To learn about bash scripting, see [http://linuxcommand.org](http://linuxcommand.org)

---

### Post by abhilashm86 on 2009-06-20
> **mali2297 said:**
> Yes. The function choose command based on the file extension. Invoke it with, for example,
```

extract something.tar.gz

```

To learn about bash scripting, see [http://linuxcommand.org](http://linuxcommand.org).

yes it works, thanks a lot...........

---

