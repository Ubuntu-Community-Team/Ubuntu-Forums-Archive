---
title: "Modify text for use with touch"
date: 2009-03-19
forum: General Help
---

### Post by mastermindg on 2009-03-19
So, I'm using offlineimap to fetch my messages to text files for processing. I've found that the most accurate method of retrieving the time stamp information is to get it from the header of the message:

```
by mail.gmx.com (mp-us004) with SMTP; 19 Mar 2009 14:20:14 -0400
```

so, by using this code:

```
cat * | grep 0400 | grep mail | cut -c41-60 | tr -d : | sed 's/ //g'
```

I have been able to turn the above into this:

```
19Mar2009142014
```

According to touch, I need it in this format:

```
touch -t 200903191420.14
```

Keep in mind that I'm using this to automate a process of comparing multiple files over time, so it won't always be March 19th.

How do I get from 19Mar2009142014 to 200903191420.14?

---

### Post by mastermindg on 2009-03-19
I figured out how to get this far:

```
19Mar20091420.14
```

```
cat * | grep 0400 | grep mail | cut -c41-60 | tr -d : | sed 's/ //g' | sed -e 's#\(.\{13\}\)\(.*\)#\1.\2#g'
```

The hard part is moving 19Mar around the other side of 2009 and translating Mar into 03, to read

```
200903191420.14
```

cat * | grep 0400 | grep mail | cut -c41-60 | tr -d : | sed 's/ //g' | sed -e 's#\(.\{13\}\)\(.*\)#\1.\2#g' | sed 's/ //g' | sed -e 's#\(.\{2\}\)\(.*\)#\1*\2#g'

---

