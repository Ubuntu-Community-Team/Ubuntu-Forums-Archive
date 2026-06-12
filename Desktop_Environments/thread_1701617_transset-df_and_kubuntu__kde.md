---
title: "transset-df and kubuntu / kde"
date: 2011-03-06
forum: Desktop Environments
---

### Post by josvanr on 2011-03-06
I just switched from ubuntu to kubuntu 10.10 and am 
trying to make everything work again. How about 
transset-df. It doesn't seem to work on kde. I tried with
and without desktop effects present. Running the program
says:

$transset-df
Set Property to 0.75

the transparency doesnt change and in the title bar menu 
it still says 'opacity: 100%'


Can this be made to work or is there any other way to 
set the transparency of a window from a script / command line?


josvanr

---

### Post by josvanr on 2011-03-07
case anyone is interested, I found this:


qdbus and qdbusviewer. Don't know exactly how this works yet, but
one can find out from those 2 how to change the opacity /transparency:



qdbus org.kde.konsole /konsole/MainWindow_1 com.trolltech.Qt.QWidget.windowOpacity 0.9


josvanr

---

### Post by josvanr on 2011-03-07
not all windows seem to have this property (eg gimp..)?...
So how set transparency for that?

---

