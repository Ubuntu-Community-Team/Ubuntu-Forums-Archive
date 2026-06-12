---
title: "desktop effect .. not enable .. (more details.)"
date: 2009-05-27
forum: General Help
---

### Post by alz3abi on 2009-05-27
Hello every body .. 

i hv a problem .. 
i cant enable desktop effect. 

i hd install Compiz . but still same .. 

in some posts i google it .. i hv found im need to install xserver-xgl 

but i cant found it on (synaptic manager). and some post contain .. go to 

system >> admin... >> Screens and graphic but i cant found it ether. 

on terminal i typed compiz but my PC fraze ! 


im sorry about my bad english .. 
and thanks in advance to enable this ..

---

### Post by alz3abi on 2009-05-27
no one ?

:(

---

### Post by taurus on 2009-05-27
What kind of graphic card does it have?  Look in System -> Administration -> Hardware Drivers to see if it's on the list.

---

### Post by alz3abi on 2009-05-27
nathing .. there :(

[IMG]http://www.almotmaiz.net/vb/upload/2_01243451905.png[/IMG]

---

### Post by alz3abi on 2009-05-27
and this is my laptop .. Toshiba A200-1MY 
[http://eu.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=EU&BV_UseBVCookie=yes&PRODUCT_ID=135206&BV_Script=/jsp/fixup/productPage](http://eu.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=EU&BV_UseBVCookie=yes&PRODUCT_ID=135206&BV_Script=/jsp/fixup/productPage)

---

### Post by DeMus on 2009-05-27
> **alz3abi said:**
> Hello every body .. 

i hv a problem .. 
i cant enable desktop effect. 

i hd install Compiz . but still same .. 

in some posts i google it .. i hv found im need to install xserver-xgl 

but i cant found it on (synaptic manager). and some post contain .. go to 

system >> admin... >> Screens and graphic but i cant found it ether. 

on terminal i typed compiz but my PC fraze ! 


im sorry about my bad english .. 
and thanks in advance to enable this ..

Open a terminal (Application menu - Accessories - terminal) and in the terminal type:
lspci | grep VGA

Select the outcome of the instruction with your mouse (highlight it) and type ctrl+shift+c (keep all 3 buttons pressed at the same time)
Paste the outcome here in your answer, so we can see what videocard you have.

---

### Post by alz3abi on 2009-05-27
> **DeMus said:**
> Open a terminal (Application menu - Accessories - terminal) and in the terminal type:
lspci | grep VGA

Select the outcome of the instruction with your mouse (highlight it) and type ctrl+shift+c (keep all 3 buttons pressed at the same time)
Paste the outcome here in your answer, so we can see what videocard you have.


00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by DeMus on 2009-05-27
> **alz3abi said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

This is what I thought. You hear many people complain about Compiz not working with the Intel graphic card.
I don't know if there is a solution already, if not, you have to forget about the effects. Sorry.

---

### Post by alz3abi on 2009-05-27
> **DeMus said:**
> This is what I thought. You hear many people complain about Compiz not working with the Intel graphic card.
I don't know if there is a solution already, if not, you have to forget about the effects. Sorry.


before 9.04 
i can use Compiz ! 
but now i cant .. 

sure there  is a solution, but i dont know where ..

---

### Post by DeMus on 2009-05-27
> **alz3abi said:**
> before 9.04 
i can use Compiz ! 
but now i cant .. 

sure there  is a solution, but i dont know where ..

If I am right, it is not Jaunty, not Compiz but the Intel driver. As I said I don't know if by now there is a solution already. Maybe somebody else knows more about it.
You could start to search here in the forums for an answer. Look for intel and driver, I'm sure you find something.

Good luck.

---

### Post by damas on 2009-06-20
This worked for me:

[http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html)

Hope it does for you.

/Damas

---

