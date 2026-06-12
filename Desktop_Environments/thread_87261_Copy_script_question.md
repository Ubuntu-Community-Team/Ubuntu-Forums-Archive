---
title: "Copy script question"
date: 2005-11-07
forum: Desktop Environments
---

### Post by christooss on 2005-11-07
How to make bash script which would do this in short:

if bmp is installed
than copy this file in ~/.bmp/
if xmms is installed
than copy this file in ~/.xmms/
if bmpx is installed
than copy this file in ~/.bmpx/

Or its even good if script would prompt for this. for example

```
(1)bmp
(2)xmms
(3)bmpx
(4)none

Type number of program which is installed on you system
```

---

### Post by ow50 on 2005-11-07
Best would probably be to check for the existence of the profile directory or the executable. To test for the existence of the executable, try the following.
```
#!/bin/bash

if [ -x "/usr/bin/xmms" ]; then
	echo "xmms installed"
else
	echo "xmms not installed"
fi
```
In this case you'd have to check at least /usr/local/bin as well. Use "-d" to check for the existence of a directory.

Even checking if you get output from "locate xmms | grep bin/" might be enough if you're lucky.

There might be easier ways as well. Maybe a way of trying to call the executable without starting the application and capturing that output?

---

### Post by NewWithoutClue on 2005-11-07
Arguments passed to the script are accessed by $0, $1, $2, $3 etc...( although argument number 10 and higher need to be in brackets ${ 10 } ${ 11 } )

Just thought I would share that...so you can also tell it what files to check for or what files to copy...or....what ever you want.

Paul.

---

### Post by Harleen on 2005-11-07
[QUOTE=ow50][...]
Even checking if you get output from "locate xmms | grep bin/" might be enough if you're lucky.

There might be easier ways as well. Maybe a way of trying to call the executable without starting the application and capturing that output?[/QUOTE]

You can get the path of an executable by "which <command>", so "which xmms" should return a path - or nothing, if it isn't installed. I changed your code a bit, so it doesn't need the path in it anymore.

```
#!/bin/bash

if [ `which xmms` ]; then
	echo "xmms installed"
else
	echo "xmms not installed"
fi

```

---

