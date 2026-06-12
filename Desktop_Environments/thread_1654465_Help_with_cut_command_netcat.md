---
title: "Help with cut command netcat"
date: 2010-12-28
forum: Desktop Environments
---

### Post by dodo3773 on 2010-12-28
So I opened a terminal and fired up netcat. I only wanted to view the Foreign Ip Addresses so I used 
```
netstat --tcp --numeric |  cut -c 45-65
```and that gave me

```




Foreign Address      
72.14.213.109:993    
66.102.7.100:80      
91.189.94.12:80      
72.14.213.109:993    
66.102.7.101:80      
91.189.94.12:80      
216.156.213.50:80    
66.102.7.101:80  
```There are two things that I am trying to accomplish here. The first is that I would like to "cut" the first three horizontal lines so that the output is only ip addresses. I tried tail but the number of different IPs changes so it still gives me those top lines. I tried head but that doesn't seem to give me any output at all. The second thing I would like to do is to filter out duplicate values. For example the output above has 2 duplicate entries of     66.102.7.101:80    I would only like to see one. If anyone could help me out at all that would be great. Thanks in advance.

---

### Post by lungten on 2010-12-28
Say your IP address list is sotered in a file called ip.txt. I am guessing you don't need the port numbers. Then, I would do something like this.

```
cat ip.txt | cut -s -d':' -f1 | sort -u
```

This will output only the delimited (-s) lines (lines containing : ) and run the output through 'sort' to get a sorted list of unique lines. You can also use the 'unique' command to get a count of occurrence of each of the duplicate lines.

---

### Post by dodo3773 on 2010-12-28
> **lungten said:**
> Say your IP address list is sotered in a file called ip.txt. I am guessing you don't need the port numbers. Then, I would do something like this.

```
cat ip.txt | cut -s -d':' -f1 | sort -u
```This will output only the delimited (-s) lines (lines containing : ) and run the output through 'sort' to get a sorted list of unique lines. You can also use the 'unique' command to get a count of occurrence of each of the duplicate lines.

O.K. So I tried 
```

netstat --tcp --numeric |  cut -s -d ':' -f1
```But it cut out the second half of the line. So I tried 
```
netstat --tcp --numeric |  cut -c 45-65 -s -d ':' -f1

```and it said "cut: only one type of list may be specified". 

When I try 
```
netstat --tcp --numeric | cut -s -d':' -f1 | sort -u

```I get
```
tcp        0      0 192.168.1.5
tcp        1      0 192.168.1.5

```Which seems to be cleaned up but I need the next field of output. I think that it is sorted the Local Address instead of the Foreign Address. It seems like we are definitely on the right track.  Also, I am doing this all from a terminal no text file at all. I would like to just use terminal output (no text file at all) if it is even possible. If it is not just let me know.

---

### Post by dodo3773 on 2010-12-28
> **lungten said:**
> Say your IP address list is sotered in a file called ip.txt. I am guessing you don't need the port numbers. Then, I would do something like this.

```
cat ip.txt | cut -s -d':' -f1 | sort -u
```This will output only the delimited (-s) lines (lines containing : ) and run the output through 'sort' to get a sorted list of unique lines. You can also use the 'unique' command to get a count of occurrence of each of the duplicate lines.


Update. So I tried 

```
netstat --tcp --numeric |  cut -c 45-65 | sort -u

```

and it gave me

```


216.156.213.50:80    
72.14.213.109:993    
Foreign Address    
```

Which did work. But now the foreign address is on the bottom instead of top and there is a blank line on top. So, it does not show duplicates but now the output is upside down.

---

### Post by robert_pectol on 2010-12-28
Lots of plumbing but here goes...
```

netstat --tcp --numeric | awk '{$1=$1}$1' | cut -d ' ' -f5 | egrep '^[1-9]' | cut -d ':' -f1 | sort | uniq

```
 You can play with the different parts to get the desired results but a quick explanation of each part follows:
**awk '{$1=$1}$1'**   removes spaces from beginning and ending of each line, including extra spaces between fields
**cut -d ' ' -f5**   selects the 5th field of each line using a single space as the delimiter
**egrep '^[1-9]'**   only prints lines that begin with a number from 1 to 9
**cut -d ':' f1**  selects the first field of each line using a colon as the delimiter
**sort**   sorts the IP addresses so that duplicates are grouped together
**uniq**  only prints unique lines (duplicate IPs are omitted)

Hope that helps a little.

---

### Post by dodo3773 on 2010-12-28
> **robert_pectol said:**
> Lots of plumbing but here goes...
```

netstat --tcp --numeric | awk '{$1=$1}$1' | cut -d ' ' -f5 | egrep '^[1-9]' | cut -d ':' -f1 | sort | uniq

``` You can play with the different parts to get the desired results but a quick explanation of each part follows:
**awk '{$1=$1}$1'**  removes spaces from beginning and ending of each line, including extra spaces between fields
**cut -d ' ' -f5**  selects the 5th field of each line
**egrep '^[1-9]'** only prints lines that begin with a number from 1 to 9
**cut -d ':' f1** selects the first field
**sort** sorts the IP addresses
**uniq** only prints unique lines (duplicate IPs are omitted)

Hope that helps a little.

Wow that worked perfectly. Thank you. I was just tinkering around with it and came up with this

```
netstat --tcp --numeric |  cut -c 45-65 | sort -u | sed '/Foreign/d' | sed '/^$/d'
```which also seemed to work. Thanks a lot you guys for all of your help. I definitely have a lot of learning to do still. Marking thread as solved. Thanks again.

---

