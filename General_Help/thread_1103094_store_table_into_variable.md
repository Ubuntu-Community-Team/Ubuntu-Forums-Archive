---
title: "store table into variable"
date: 2009-03-22
forum: General Help
---

### Post by DeepSeaNautilus on 2009-03-22
Hello, I want to store several tables in variables to make several replacements inside a file.

for example
```
cat table1
1 one
2 two
3 three
```

```
cat table2
4 four
5 five
6 six
```

```
cat mainFile
<some text>
replacePattern1
<some text>
replacePattern2
<some text 3>
```

I am doing this:
```
var1=`cat table1`
var2=`cat table2`
sed 's/replacePattern1/"$var1"/g' mainFile
sed 's/replacePattern2/"$var2"/g' mainFile
```

The problem is that when I assign tablex command output to the variable varx it replaces the newline characters for blank character.
```

echo "$var1"
1 one 2 two 3 three
```

Is there any way to keep the newline characters, so it can keep its original format?

---

