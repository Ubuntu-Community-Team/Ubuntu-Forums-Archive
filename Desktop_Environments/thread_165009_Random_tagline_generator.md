---
title: "Random tagline generator"
date: 2006-04-23
forum: Desktop Environments
---

### Post by drfox on 2006-04-23
Does anyone have a recommendation for a GPL random tagline generator that would attach my signature and a tagline to outgoing email.

Thanks.

Larry

---

### Post by Fluffball on 2008-02-17
I wanted something quick to do this and realised it doesn't require a program to do it. A small script can achieve the same thing:

Have a file containing one line tag lines, e.g. called "Taglines.txt"

1.
a) Create a script called something like "random_tagline" with the following:
echo > $2
echo "Name" >> $2
echo "--" >> $2
echo "name@address.com" >> $2
echo "---" >> $2

line=`wc -l $1 | awk 'BEGIN {srand ()} {print int(rand() * $0)}'`
egrep -v '#' $1 | awk '{print count++"|"$0}' | egrep "^$line\|" | cut -d\| -f2- >> $2

b) chmod +x random_tagline

2. Crontab -e

3. Edit crontab so it looks something like this (change the update time as you see fit, this is every 5 minutes):
# m h  dom mon dow   command
0,5,10,15,20,25,30,35,40,45,50,55 0-23 * * * /<path to script>/random_tagline /<path to tag line file>/Taglines.txt /<path to file which is read by email program>/sig-default.txt

Enjoy! :)

---

