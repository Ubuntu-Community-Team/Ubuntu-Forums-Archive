---
title: "Beta 9.10 can't send email with attachment using mutt"
date: 2009-10-21
forum: Desktop Environments
---

### Post by marek23 on 2009-10-21
Welcome,

I have following problem with my desktop working under 9.10 Beta.


On my 8.04 i had using mutt for sending email with attachment.
Now i can't get it to work.

When i try execute following command

```
 mutt -a 'test.txt' -s 'subject' admin@xxx.com <'test'
```i got answer
```
bash: test: No such file or directory
```But the ls shows 

```
/tmp/test$ ls
test.txt

```If anyone have idea whats wrong please help.

Version
```
mutt -h
Mutt 1.5.20 (2009-06-14)
```


Also my scripts, what previous working perfect now stops.

I dont know is this foult of invalid mutt compilation, maybye somebody can try on own box in 9.10 send attachment, maybye i have to downgrade my mutt.


Regards

---

