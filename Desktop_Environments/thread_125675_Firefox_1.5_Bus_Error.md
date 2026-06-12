---
title: "Firefox 1.5 Bus Error"
date: 2006-02-04
forum: Desktop Environments
---

### Post by happyponcho42 on 2006-02-04
Although I have made great use of the SessionSaver extention, the crashes are occuring more often at random times and becoming very annoying.

Whenever firefox crashes, I get the following variations of errors in the console:

```
/opt/firefox/run-mozilla.sh: line 131: 30589 Bus error          "$prog" ${1+"$@"}
```

```
/opt/firefox/run-mozilla.sh: line 131: 14571 Segmentation fault          "$prog" ${1+"$@"}
```


```
/opt/firefox/run-mozilla.sh: line 131: 9523 Segmentation fault          "$prog" ${1+"$@"}
```

lines 130-198:
```
moz_run_program()
{
	prog=$MOZ_PROGRAM
	##
	## Make sure the program is executable
	##
	if [ ! -x "$prog" ]
	then
		moz_bail "Cannot execute $prog."
	fi
	##
	## Use md5sum to crc a core file.  If md5sum is not found on the system,
	## then dont debug core files.
	##
	moz_test_binary /bin/type
	if [ $? -eq 1 ]
	then
		crc_prog=`type md5sum 2>/dev/null | awk '{print $3;}' 2>/dev/null | sed -e 's/\.$//'`
	else
		crc_prog=`which md5sum 2>/dev/null`
	fi
	if [ -x "$crc_prog" ]
	then
		DEBUG_CORE_FILES=1
	fi
	if [ "$DEBUG_CORE_FILES" ]
	then
		crc_old=
		if [ -f core ]
		then
			crc_old=`$crc_prog core | awk '{print $1;}' `
		fi
	fi
	##
	## Run the program
	##
	"$prog" ${1+"$@"}
	exitcode=$?
	if [ "$DEBUG_CORE_FILES" ]
	then
		if [ -f core ]
		then
			crc_new=`$crc_prog core | awk '{print $1;}' `
		fi
	fi
	if [ "$crc_old" != "$crc_new" ]
	then
		printf "\n\nOh no!  %s just dumped a core file.\n\n" $prog
		printf "Do you want to debug this ? "
		printf "You need a lot of memory for this, so watch out ? [y/n] "
		read ans
		if [ "$ans" = "y" ]
		then
			debugger=`moz_get_debugger`
			if [ -x "$debugger" ]
			then
				echo "$debugger $prog core"

				# See http://www.mozilla.org/unix/debugging-faq.html
				# For why LD_BIND_NOW is needed
				LD_BIND_NOW=1; export LD_BIND_NOW

				$debugger "$prog" core
			else
				echo "Could not find a debugger on your system."
			fi
		fi
	fi
}
```

Can anyone help me with this issue?

---

