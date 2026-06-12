---
title: "Using sed and read together"
date: 2009-06-09
forum: General Help
---

### Post by siuchi on 2009-06-09
I have the following little script to help me delete a line from a file.

sed -n -i '16!p' FILE_NAME

And i want to make some change, so it would ask for which number to delete. And I tried to change the script a bit to like this. But does not work, can anyone tell me which part i have done wrong. Many of Thanks.


#/bin/sh
echo "Please enter the line to delete"
read line
sed -n '\$line!p' testing

---

### Post by x22 on 2009-08-15
this seems to work OK:

#/bin/sh
echo "Please enter the line to delete"
read line
sed "$line"d <testing

---

### Post by kaibob on 2009-08-16
This also works:

```
#!/bin/bash
read -p "Line to delete: " line
sed -i ${line}d file
```

EDIT: I just noticed that the original post is over 2 months old. I think the OP has resolved this issue one way or another.

---

