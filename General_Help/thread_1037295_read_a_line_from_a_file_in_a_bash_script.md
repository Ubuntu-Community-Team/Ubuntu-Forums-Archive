---
title: "read a line from a file in a bash script"
date: 2009-01-11
forum: General Help
---

### Post by LeChacal on 2009-01-11
I am trying to write a script and I need to read a line from another file. The file is a list of data, one item (word) per line. What command can I use to read just the line that I want and then pass that data to another command? Thank You

---

### Post by mike2357 on 2009-01-11
```
read my_line < my_input_file.txt
```
You can test this with
```
echo $my_line
```

---

### Post by heindsight on 2009-01-11
> **mike2357 said:**
> ```
read my_line < my_input_file.txt
```

this will always read the first line from the file.
you can read the file one line at a time by doing:
```

cat file | while read line; do
    # put whatever you want to do to each line of the file here
done

```

or if you want only the n'th line of the file, do
```
line=$(sed -ne "$n p" file)
```

or if you want the first line containing a specific bit of text you could do: ```
line=$(grep -m 1 'text you're searching for' file)
```
You could also drop the '-m 1' and use grep in combination with the two previous examples to get the n'th line containing a specific bit of text or all lines containing that text (one at a time).

---

### Post by SeanHodges on 2009-01-11
> **heindsight said:**
> cat file | while read line; do
    # put whatever you want to do to each line of the file here
done


This is valid, but you can avoid running the "cat" program altogether by doing:

```
while read line
do
    echo $line
    # Do other things with $line
done < "my_input_file.txt"
```

---

### Post by LeChacal on 2009-01-14
Sorry about the long response time i got side tracked. Thank you heindsight 

```
sed -ne "$n p" file
```

was what i need, i had never heard of "sed" before.

---

### Post by dagnabit dang doohickey on 2009-01-14
```
awk 'NR == *line*' *input-file*
```

---

