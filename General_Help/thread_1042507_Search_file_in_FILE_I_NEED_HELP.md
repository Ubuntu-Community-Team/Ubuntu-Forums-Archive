---
title: "Search file in FILE I NEED HELP"
date: 2009-01-17
forum: General Help
---

### Post by just_linux on 2009-01-17
I have a file " lets call it DICTIONARY" it has some words "no duplicates and sorted. each line only got on line"
NOW I have a other file that got words in each line as well sorted and each line got one word only "WORDS" 
NOW how can I do spell check .ei: I could see which words are in the WORDS file which are not in DIC???

Thanks a lot 
IT IS VERY IMPORTANT FOR ME 
PS: I know I need to use" comm " but I do not know how u may look at it

---

### Post by ac7ss on 2009-01-17
man comm

comm -13 dict.txt doc.txt

should show only the words in the doc.txt that are not in dict.txt

---

