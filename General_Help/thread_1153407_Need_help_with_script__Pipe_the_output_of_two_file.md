---
title: "Need help with script : Pipe the output of two files into one command"
date: 2009-05-08
forum: General Help
---

### Post by generic_idea_machine on 2009-05-08
I have a simple script that extracts some data from a website and mails it out. I am trying to incorporate a disclaimer towards the end of the script, some text and a link to another site. Having a bit of a problem incorporating the latter though:

here is the code I am using. 

```
#!/bin/bash
DATE=`date +%e-%m-%y`

#Purpose : Extract the gas price from a given website and email it to a pre-defined list of recipients


#Subject and recipient variables
subject="Tomorrow's Gas Price, Today"

sendto="jenkuya@robomail.com"



lynx -dump http://www.mcteague.ca/WebPages/gas_price_chart.htm| grep -i "The price of gasoline for\|London\*\|Waterloo" > /tmp/gas-prices.txt

cd /tmp


mail -s "$subject-$DATE" $sendto </tmp/gas-prices.txt 

```

Suppose the Disclaimer page I am referring to is [http://wolverine/gas](http://wolverine/gas)
How would I place that link in my outgoing email along with a little bit of a text. Should I use xargs or setup a variable in order to do this. And if so, then how...

Any help would be greatly appreciated. thanks!

---

### Post by generic_idea_machine on 2009-05-08
Found the solution

a relatively simple one

cat file1 file2 |mail -s "xyvxvx" $recipient

---

