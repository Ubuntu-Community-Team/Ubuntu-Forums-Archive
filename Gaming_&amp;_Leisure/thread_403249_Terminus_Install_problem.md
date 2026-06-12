---
title: "Terminus Install problem"
date: 2007-04-06
forum: Gaming &amp; Leisure
---

### Post by cogadh on 2007-04-06
I have this old space combat RPG called Terminus that came with Windows Mac and Linux install routines. When I try to run the install script in Ubuntu Edgy, I get the following non-informative error:
```
cogadh@cogadh-desktop:/media/cdrom$ sudo sh Linux_Install
Linux_Install: 9: function: not found
x86

```

I checked through the install script and I think the error occurs on this:
```
# Return the appropriate architecture string
function DetectARCH {
	status=1
	case `uname -m` in
		i?86)  echo "x86"
			status=0;;
		*)     echo "`uname -m`"
			status=0;;
	esac
	return $status
}
```

What I can't figure out is what it should be finding when it is looking to determine the correct architecture. Anyone have any ideas?

---

### Post by Phenax on 2007-04-06
```

sudo bash Linux_Install

```
or
```

chmod +x Linux_Install
./Linux_Install

```

Just a guess.

The problem is that Ubuntu (I've not used it in years!) links /bin/sh to /bin/dash or something similar. Probably done because Bash is much slower at many things. Dash and Bash don't have the same scripting functionalities. Dash may not support functions (It's not the actual stuff inside the function that matters, but rather that it IS a function).

I might be mistaken about Dash, or about this at all..

---

### Post by cogadh on 2007-04-06
That worked. Now I remember having to use bash when I first installed it on Red Hat 6 years ago. 

Of course now the game won't launch. First it was a problem with the old (really old) libstdc++ library not installed, solved that with a symbolic link to the new library, but now it gives me this error:
```
terminus: symbol lookup error: terminus: undefined symbol: cerr
```
If anybody has managed to get this game actually running in Ubuntu, I'd appreciate any and all advice on how they did it.

Oh, almost forgot, I did already apply the latest official patch but none of the TPE patches.

---

### Post by cogadh on 2007-04-09
Nobody has any ideas?

---

### Post by leech on 2007-04-16
I was thinking about installing this game again as well.  If I recall, I had to install the TPE patches to get it to work before, since it links with newer libraries.

If I can actually locate my install disks, I'll give it a shot sometime in the upcoming weeks, but try out the TPE patches.

Leech

---

### Post by cogadh on 2007-04-18
I finally had the chance to work on this and apparently the TPE patch does change some of the linking, because now I have a different library showing up as missing:
```
TPE-MDK8-V0-04: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```
Usually I'm pretty confident when it comes to creating new symbolic links to cover problems like this, but on this one I'm stumped. What library is it looking for, part of the libstdc++ library or the libc6 library?

---

