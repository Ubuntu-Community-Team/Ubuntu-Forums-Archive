---
title: "Herpes3 Loki problem"
date: 2007-03-11
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2007-03-11
when I run setup.sh I get :

maxim@maxim:/media/cdrom0$ sudo sh setup.sh
setup.sh: 9: function: not found
x86

here is the setup.sh file :


```
#!/bin/sh
#
# Product setup script - Loki Entertainment Software

# Go to the proper setup directory (if not already there)
cd `dirname $0`

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

# Return the appropriate version string
function DetectLIBC {
      status=1
      if [ -f `echo /lib/libc.so.6* | tail -1` ]; then
	      if fgrep GLIBC_2.1 /lib/libc.so.6* 2>&1 >/dev/null; then
	              echo "glibc-2.1"
	              status=0
	      else    
	              echo "glibc-2.0"
	              status=0
	      fi        
      elif [ -f /lib/libc.so.5 ]; then
	      echo "libc5"
	      status=0
      else
	      echo "unknown"
      fi
      return $status
}

# Detect the Linux environment
arch=`DetectARCH`
libc=`DetectLIBC`

# Find the installation program
function try_run
{
    setup=$1
    shift
    fatal=$1
    if [ "$1" != "" ]; then
        shift
    fi

    # First find the binary we want to run
    failed=0
    setup_bin="setup.data/bin/$arch/$libc/$setup"
    if [ ! -f "$setup_bin" ]; then
        setup_bin="setup.data/bin/$arch/$setup"
        if [ ! -f "$setup_bin" ]; then
            failed=1
        fi
    fi
    if [ "$failed" -eq 1 ]; then
        if [ "$fatal" != "" ]; then
            cat <<__EOF__
This installation doesn't support $libc on $arch

Please contact Loki Technical Support at support@lokigames.com
__EOF__
            exit 1
        fi
        return $failed
    fi

    # Try to run the binary
    # The executable is here but we can't execute it from CD
    setup="$HOME/.setup$$"
    cp "$setup_bin" "$setup"
    chmod 700 "$setup"
    if [ "$fatal" != "" ]; then
        "$setup" $*
        failed=$?
    else
        "$setup" $* 2>/dev/null
        failed=$?
    fi
    rm -f "$setup"
    return $failed
}


# Try to run the setup program
status=0
rm -f "$setup"
if ! try_run setup.gtk && ! try_run setup -fatal; then
    echo "The setup program seems to have failed on $arch/$libc"
    echo
    echo "Please contact Loki Technical Support at support@lokigames.com"
    status=1
fi
exit $status

```

I use Ubuntu Edgy
help please ?

P.S
could someone please change my thread title to "Heroes3 Loki Problem" ?

---

### Post by MaximB on 2007-03-12
please can someone rename the thread title, it looks so absurd.

---

### Post by MaximB on 2007-03-13
can someone help please ? (and change the title too)

---

### Post by Matrix101 on 2007-03-13
Im not sure but maybe you find something in this thread:
[http://www.ubuntuforums.org/showthread.php?t=189360&highlight=heroes+3](http://www.ubuntuforums.org/showthread.php?t=189360&highlight=heroes+3)

---

### Post by MaximB on 2007-03-14
Thanks but i'm stuck at the "sudo sh setup.sh" part as you can see.

---

### Post by Matrix101 on 2007-03-14
Maybe it does not work because edgy is too "new". The loki games are somewhat old and so are their installers. As seen on the starting of setup the function at the 9th line cant be found. This can be because the terminology of the bash changed are something in that way. You could try to install libdistcc if it isnt installed yet or an older version of glibc.

---

### Post by MaximB on 2007-03-14
> **Matrix101 said:**
> Maybe it does not work because edgy is too "new". The loki games are somewhat old and so are their installers. As seen on the starting of setup the function at the 9th line cant be found. This can be because the terminology of the bash changed are something in that way. You could try to install libdistcc if it isnt installed yet or an older version of glibc.

I've installed "glibc" but I can't find "libdistcc".
the setup won't run

---

### Post by Matrix101 on 2007-03-14
Try distcc

---

### Post by MaximB on 2007-03-14
downloaded and installed the packages, but to no avail.
I'm still stuck
maybe I should edit the setup.sh ?

---

### Post by chaggydawg on 2007-06-20
have you tried

```
bash ./setup.sh
```

it worked for me

---

### Post by MaximB on 2007-06-20
Thanks, it's weird but it's actually worked.
I don't know the difference between "sudo sh setup.sh" and "sudo bash ./setup" ...strange...

is there a way to run all the expansions natively ?

---

