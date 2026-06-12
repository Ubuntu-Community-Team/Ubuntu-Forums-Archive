---
title: "Getting past being blocked by the exicutable bit"
date: 2011-03-06
forum: Gaming &amp; Leisure
---

### Post by DarbyCrash on 2011-03-06
So i installed  java left clicked mine craft.jar  and pressed run with sun java 6 runtime have . it then says "The file '/home/maklane/Downloads/minecraft (1).jar' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the executable bit" how do i get past this if i am doing it right i just want too be able to play minecraft. remember im a begginer so make it basic ahha. any help would be greatly appreciated also if you know the names of any guides that are good for a begginer

---

### Post by Nutbun on 2011-03-06
install java runtime from your package manager
Download the Linux version of minecraft from the site. 
Right click the downloaded minecraft.jar then select properties then 'permissions' tab, tick 'allow executing file as program'.
Go to 'Open with' tab and select java. 
I think you have to have the additional graphics drivers installed as well.
And that's it, double click your minecraft.jar and your away.

It will install itself to your home folder ./minecraft
You will need to view hidden files to see it.

---

### Post by Largenumber on 2011-03-06
What you need to do is:
1.) Right click on the .jar file.
2.) Select properties.
3.) Under permissions. Check the allow executing file as program.
4.) ????
5.) Profit

Also, there is no need to make 2 threads on the same topic.

---

### Post by DarbyCrash on 2011-03-06
yes that worked!!

---

### Post by kn0w-b1nary on 2011-03-07
Or in terminal type:
```
cd /path/to/file
```
```
chmod +x filename
```

---

