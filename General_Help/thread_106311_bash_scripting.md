---
title: "bash scripting"
date: 2005-12-20
forum: General Help
---

### Post by Lofticus on 2005-12-20
Hi People!

I want to make a bash script, that does following:

I have 3 scripts, all for wlan, which just does ifconfig eth1 essid blabla etc. blabla called school.sh or home.sh or xyz.sh

So what I want to do is that the script makes an iwlist scan and then searches the results. f.e. if the wireless network called ACER is found, it shell connect to ACER, else connect to school, else connect to xyz.

Anyone has an idea how this can be made?

I think an iwlist scan | grep <termtosearch> should do the trick, but I'm just not good enough, and even if thats the trick, I don't know how to write that whole thing. 

Anyone can help me with this?

Thanks, 

Lofticus

---

### Post by mgor on 2005-12-20
```
#!/bin/sh

interface="eth1"
for ap in `iwlist ${interface} scanning | grep ESSID | awk -F\" '{print $2}' | uniq`
do
	case "$ap" in
		"xyz" )	sh xyz.sh; break;;
		"home" ) sh home.sh; break;;
		"school" ) sh school.sh; break;;
		* ) echo "No valid ESSID's found"; break;;
	esac
done
```

should do the trick :-)

btw, [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) is a good resource for bash scripting.

---

### Post by Lofticus on 2005-12-20
thank you, I will test it tomorrow.

Can I make sh wlan/xyz.sh; break;; instead of sh xyz.sh?

TYAL

Lofticus

---

### Post by Lofticus on 2005-12-20
it works, ty a lot!

(maybe you can explain what those commands mean if you have time? *g*)

Lofticus

---

### Post by mgor on 2005-12-21
great! glad i could help, sat and waited on an airport, had some time over before my plane depatured, so i didn't too have much todo ;-)

```
iwlist ${interface} scanning | grep ESSID | awk -F\" '{print $2}' | uniq
```

takes the output from `iwlist`, searches for every line that contains the line ESSID, splits every line at any "-chars to seperate strings and prints the second string. If you run the command without `awk` you'll se that it prints something like
```
ESSID:"something"
```

the `uniq` command just make sure that only one occurance of a string will take place, you might get accesspoint overlaps, so you'll se more then one occurance of every essid.

```
for ap in `iwlist ${interface} scanning | grep ESSID | awk -F\" '{print $2}' | uniq`
```

basiclly says 'for every line in the output, assign the value to ap and do something with it before proceding to the next line'.

the 'case'-part is just like any switch-case statement, if $ap has either of the values, execute the script and stop the for-loop.

as i mentioned in my first post, [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) is a _great_ resource for bash-scripting.

---

### Post by Lofticus on 2005-12-22
ok thank you (-: I will read through that link if I can find myself some time (-:

nice work (:

---

