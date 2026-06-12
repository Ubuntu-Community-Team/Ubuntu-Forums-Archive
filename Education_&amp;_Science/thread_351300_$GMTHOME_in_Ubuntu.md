---
title: "$GMTHOME in Ubuntu?"
date: 2007-02-01
forum: Education &amp; Science
---

### Post by timmie on 2007-02-01
Hi!

As you may know there's a bug in the [GMT]("https://launchpad.net/ubuntu/+source/gmt/+bug/54891") package. There fore I am somehow lost.

to which directory do I have to set the GMTHOME in Ubuntu?

Thank you very much!

Timmie

---

### Post by timmie on 2007-02-02
With [this site]("http://acd.ucar.edu/~fredrick/linux/gmt/") I got to know how to set it:

```

##Path for netcdf & GMT
export NETCDFHOME=/usr/lib
NETCDF_PREFIX=$NETCDFHOME
GMTHOME=/usr/lib/gmt
export GMTHOME
PATH="$PATH:$GMTHOME/bin"
export PATH
MANPATH="$MANPATH:$GMTHOME/man"
export MANPATH

```

setting it like
```

#gmt variables

export NETCDFHOME="/usr/lib"

export GMTHOME="/usr/lib/gmt"

export PATH="$PATH:$GMTHOME/bin"

```
didn't work for me.

So long.

---

### Post by apienk01 on 2007-08-29
GMT works perfectly in Ubuntu, but you have to use the wrapper script. Just precede any GMT command with 'GMT', for example:
```
GMT pscoast -R-30/330/-75/75 -Jm0.03c -Ba30g30 -G0/128/0 -S255/255/255 -A5000 -P
```

---

