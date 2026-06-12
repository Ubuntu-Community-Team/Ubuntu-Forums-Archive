---
title: "Skype on dell d620"
date: 2009-03-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chrisstuck on 2009-03-20
I am new to this and have lots to learn . I have installed ubuntu 8.10 in a dual install with windows so I can carry on using the laptop while I learn about this . 
However the catch is my net connection works much better under ubuntu that xp but I can not install skype . When I boot straight from the cd , I can install skype no problem . When I try from the installed version I get 

error:dependency is not satisfiable : lib4-core 

Anyone have any idea what I need to do ? 

Thanks

Chris

---

### Post by kaixi on 2009-03-21
If you have the .deb package I suggest you try installing it from the terminal:
```

cd *name_of_the_folder_where_the_package_is_located*

sudo dpkg -i *whatever*.deb
```


now let's fix the broken dependency thing. open the terminal again and type:
```

sudo aptitude -f install
```

---

### Post by chrisstuck on 2009-03-22
Thanks
Ran the fix line and it sorted out whatever was stopping the install . 

One day I will know what it did .

Thanks

Chris

---

