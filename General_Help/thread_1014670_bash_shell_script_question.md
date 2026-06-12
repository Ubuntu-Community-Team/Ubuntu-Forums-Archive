---
title: "bash shell script question"
date: 2008-12-18
forum: General Help
---

### Post by pwaugh on 2008-12-18
If I do this:

```

#! /bin/bash

# sha1 - computes sha1 hash for Blackberry

if [ $# -eq 0 ]
	then
		echo "Usage: sha1 [-bb] string" 1>&2
		exit 1
fi

if [ $# = 1 ]
	then
		str="${1}"
	else
		str="${2}"
fi

echo -n "${1}: "
echo -n "net.berrysoft.dib.Game" | gpg --print-md sha1

digest="$(echo -n ${str} | gpg --print-md sha1)"

if [ ! "${1}" = "-bb" ]
	then
		echo ${digest}
	else
		# Show Blackberry sha1
		echo "Blackberry sha1 here"
fi

exit 0

```

patrick@berrysoft:~$ sha1 net.berrysoft.net.dib.Game
net.berrysoft.net.dib.Game: 3BAA 19CE F8E6 D0E4 2464  196F 05DA D75C 426E 3851
8799 5643 2A92 5D50 B804 369B FFA4 9734 E022 B92D
patrick@berrysoft:~$

You can see that the hashes produced are different!  Why?  How can I get the second to display the correct value of the first??

Patrick

---

