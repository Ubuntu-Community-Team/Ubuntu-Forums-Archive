---
title: "office documents in gnome office"
date: 2009-04-30
forum: General Help
---

### Post by Dawei87 on 2009-04-30
i am curious, i want to rid myself of windows but i am still recquired to use so microsoft office at school and such. i prefer using abiword and gnumeric, can i use these instead and have all the features i would need in windows? if so, my next question is how do i make abiword use .doc as default format? when i type something and then save as .doc it says i will lose formatting and then it doesnt look good in micorsoft office. i always hear that openoffice and gnome office work well with microsoft, but i havent figured out how. any help would be much appreciated.

---

### Post by ajgreeny on 2009-04-30
Go to your hidden ~/.AbiSuite folder and open the abiword.profile in gedit.
Look for the lines with the following in:-
```
<Scheme
        name="_custom_"
        ZoomPercentage="88"
         />
```and add a line so it looks like this
```
<Scheme
        name="_custom_"
        ZoomPercentage="88"
        DefaultSaveFormat=".doc"
        />
```Save the file and it should now work by default, saving as .doc.

---

### Post by Dawei87 on 2009-04-30
thank you so much! i feel like that should be a setting under preferences. so if i do this, it wont give me any formatting problems, correct?

---

### Post by Sef on 2009-04-30
> so if i do this, it wont give me any formatting problems, correct?

Usually no, but depends on what fonts each os is using.

---

### Post by Dawei87 on 2009-04-30
thats great. and thanks again! i only have two more small hurdles now...

---

