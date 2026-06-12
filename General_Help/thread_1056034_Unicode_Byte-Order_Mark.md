---
title: "Unicode Byte-Order Mark"
date: 2009-01-31
forum: General Help
---

### Post by Man_Beach on 2009-01-31
I was checking a page from my website on the W3C markup validation site and it came up with a warning

"Byte-Order Mark found in UTF-8 File.
The Unicode Byte-Order Mark (BOM) in UTF-8 encoded files is known to cause problems for some text editors and older browsers. You may want to consider avoiding its use until it is better supported."

Any idea what it means, how it might have got there and how I can remove it? Most of the page was produced with gedit, but some of the text would have been produced at work using Microsoft Notepad and pasted in.

---

### Post by tjeck46 on 2010-04-16
You can remove BOM with gedit by copying all exept the first line from original file into the new file (start by inserting a newline in the top of the original file). Then overwrite the old file with the new one. Done. :-)

---

### Post by rduke15 on 2010-07-31
Many solutions:

uconv:
```
sudo apt-get install libicu-dev
uconv  --remove-signature BOM-FILE > NOBOM-FILE

```

awk (from [this site]("http://www.linuxask.com/questions/how-to-remove-bom-from-utf-8")):
```
awk '{if(NR==1)sub(/^\xef\xbb\xbf/,"");print}' BOM-FILE > NOBOM-FILE
```

sed:
```
sed -e '1s/^\xef\xbb\xbf//' BOM-FILE > NOBOM-FILE
```
or to convert the file in-place:
```
sed -i -e '1s/^\xef\xbb\xbf//' BOM-FILE
```
or in-place with a backup:
```
sed -i.bak -e '1s/^\xef\xbb\xbf//' BOM-FILE
```

You can make an alias:

```
alias killbom='sed -i -e "1s/^\xef\xbb\xbf//"'
```
so that you can convert the files in-place with
```
killbom BOM-FILE
```

---

