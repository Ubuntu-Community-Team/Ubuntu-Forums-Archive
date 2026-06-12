---
title: "OpenBox remembering position for pidgin"
date: 2009-05-22
forum: General Help
---

### Post by NotLikingIt on 2009-05-22
Hi, I decided to try out OpenBox, and I'm liking it so far

but I'm having trouble with remembering positions

For example, I have pidgin set to show up on the right side of the screen,undecorated

and I made it very narrow, the problem is, when I initiate an IM, the window also takes on the setting for the pidgin main window

Is there anyway to seperate them?

this is what I have in my rc.xml
```

  <applications>
   <application name = "pidgin">
   <decor>no</decor>
   <shade>no</shade>
   <layer>normal</layer>
   <position>
     <x>930</x>
     <y>40</y>
    </position>
     </application>

```

Thanks in advance

---

### Post by NewWorld on 2011-03-04
I don't think that's possible with OpenBox.

However, you can write a wrapper script for Pidgin and use the program 'wmctrl'.

---

### Post by m_duck on 2011-03-04
Run the following command in the terminal, then click your contacts window. Then run it again and click a conversation window. If the results are different, then you will be able to specify them individually, however if they are the same, I'm not sure it would be possible.
```
xprop | grep WM_CLASS
```
The above should give you the name and class of each window you click on, which you can then use to refer to the respective windows.

Apologies if this is a bit vague... I am without a Linux box at present.

---

### Post by urukrama on 2011-03-04
That is indeed possible, as m_duck has described. In case the class is the same, you can also use the "role" value of the application, which you can find with the following command:

```
xprop | grep "ROLE"
```

Not all applications have a ROLE value, but pidgin might. You then add specify this in your rc.xml file as follows: <application name="NAME" class="CLASS" role="ROLE">.

---

