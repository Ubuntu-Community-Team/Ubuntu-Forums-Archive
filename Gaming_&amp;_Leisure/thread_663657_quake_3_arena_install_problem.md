---
title: "quake 3 arena install problem"
date: 2008-01-10
forum: Gaming &amp; Leisure
---

### Post by residentevil on 2008-01-10
hi !
I tried to install Quake III arena for my ubuntu, but when a run setup.sh file it returns me an error :
root@UmBrElLaCorp2007:/mnt/dvd# ./setup.sh
./setup.sh: 9: function: not found
x86

i try sh setup.sh, but there is no difference !
I've opened *.sh file, there i found this peace of code :

function DetectARCH {
        status=1
        case `uname -m` in
                [SIZE="6"]i?86)  echo "x86"[/SIZE]
                        status=0;;
                *)     echo "`uname -m`"
                        status=0;;
        esac
        return $status
}

this is the problem, but i can not understand what is this function x86 :confused:

---

### Post by Sockerdrickan on 2008-01-10
I would recommend getting an installer of the improved Quake III here [www.ioquake3.org](www.ioquake3.org)

---

### Post by residentevil on 2008-01-10
some other idea's ?

---

### Post by chm0d on 2008-01-10
ioquake3 is your best bet.  I have installed q3 many times and it really isn't difficult.  The only thing I dont like is you can't play any punkbuster servers.  It's just not supported ;( 

fsckr

---

### Post by LeDechaine on 2008-02-09
Hmm. I think **residentevil** is refering to the Quake 3 Arena Demo.

I've encountered the exact same problem yesterday after executing the setup.sh from the demo installation.

Sorry if i'm wrong. ;)

---

