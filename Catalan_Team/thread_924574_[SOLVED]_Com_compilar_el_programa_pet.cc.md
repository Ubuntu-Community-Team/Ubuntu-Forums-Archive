---
title: "[SOLVED] Com compilar el programa pet.cc"
date: 2008-09-19
forum: Catalan Team
---

### Post by tanreb20 on 2008-09-19
Hola! Algu em podria explicar com compilar l'arxiu adjunt?

Se suposa que és un C pero quan intento compilar-lo no em surt...

Us deixo el resultat del gcc:

```
bernat@portatil:~/firefox/pet-1.0$ sudo gcc pet.cc 
[sudo] password for bernat: 
pet.cc:33:18: error: glib.h: No such file or directory
pet.cc:34:21: error: gtk/gtk.h: No such file or directory
pet.cc:35:45: error: gdk-pixbuf-xlib/gdk-pixbuf-xlib.h: No such file or directory
pet.cc:48: error: ‘gint’ does not name a type
pet.cc:51: error: ‘gint’ does not name a type
pet.cc:52: error: ‘guint’ does not name a type
pet.cc:53: error: ‘guint’ does not name a type
pet.cc:54: error: ‘guint’ does not name a type
pet.cc:58: error: ISO C++ forbids declaration of ‘GdkPixbuf’ with no type
pet.cc:58: error: expected ‘;’ before ‘*’ token
pet.cc:61: error: ‘guint’ does not name a type
pet.cc:66: error: ‘guint’ does not name a type
pet.cc:71: error: ‘guint’ does not name a type
pet.cc:78: error: ‘guint’ does not name a type
pet.cc:79: error: ‘gboolean’ does not name a type
pet.cc:81: error: ‘guint’ does not name a type
pet.cc:94: error: ‘guint’ has not been declared
pet.cc:94: error: ‘guint’ has not been declared
pet.cc:95: error: ‘guint’ has not been declared
pet.cc:95: error: ‘guint’ has not been declared
pet.cc:96: error: ‘gboolean’ does not name a type
pet.cc:97: error: ‘gboolean’ does not name a type
pet.cc:99: error: ‘gboolean’ does not name a type
pet.cc:103: error: ‘gboolean’ does not name a type
pet.cc: In function ‘int x_error(Display*, XErrorEvent*)’:
pet.cc:120: error: ‘g_error’ was not declared in this scope
pet.cc: At global scope:
pet.cc:129: error: ‘guint’ has not been declared
pet.cc:129: error: ‘guint’ has not been declared
pet.cc: In function ‘void x_init(XWindow*, int, int)’:
pet.cc:132: error: ‘g_error’ was not declared in this scope
pet.cc:136: error: ‘struct XWindow’ has no member named ‘screen’
pet.cc:137: error: ‘struct XWindow’ has no member named ‘depth’
pet.cc:137: error: ‘struct XWindow’ has no member named ‘screen’
pet.cc:138: error: ‘struct XWindow’ has no member named ‘screen’
pet.cc:141: error: ‘struct XWindow’ has no member named ‘x’
pet.cc:141: error: ‘struct XWindow’ has no member named ‘y’
pet.cc:142: error: ‘struct XWindow’ has no member named ‘root_width’
pet.cc:142: error: ‘struct XWindow’ has no member named ‘root_height’
pet.cc:143: error: ‘struct XWindow’ has no member named ‘border’
pet.cc:143: error: ‘struct XWindow’ has no member named ‘depth’
pet.cc:147: error: ‘struct XWindow’ has no member named ‘depth’
pet.cc:149: error: ‘struct XWindow’ has no member named ‘screen’
pet.cc:149: error: ‘gdk_pixbuf_xlib_init’ was not declared in this scope
pet.cc: At global scope:
pet.cc:161: error: ‘guint’ has not been declared
pet.cc:161: error: ‘guint’ has not been declared
pet.cc:173: error: ‘gboolean’ does not name a type
pet.cc:202: error: ‘gboolean’ does not name a type
pet.cc:294: error: variable or field ‘xml_start_element’ declared void
pet.cc:294: error: ‘GMarkupParseContext’ was not declared in this scope
pet.cc:294: error: ‘context’ was not declared in this scope
pet.cc:295: error: expected primary-expression before ‘const’
pet.cc:296: error: expected primary-expression before ‘const’
pet.cc:297: error: expected primary-expression before ‘const’
pet.cc:298: error: ‘gpointer’ was not declared in this scope
pet.cc:299: error: ‘GError’ was not declared in this scope
pet.cc:299: error: ‘error’ was not declared in this scope

```

---

### Post by papapep on 2008-09-19
I allà on l'has obtingut no tens informació sobre les dependències? ni tan sols expliques què és ni d'on has tret el programa....no ens ajudes gaire a ajudar-te.

I, si et mires el fitxer pet.cc, a dins hi diu (línies 22 i 23):

```
// Compile line:
// g++ -Wall pet.cc `pkg-config gtk+-2.0 gdk-pixbuf-xlib-2.0 --cflags` `pkg-config  gtk+-2.0 gdk-pixbuf-xlib-2.0 --libs` -o pet
```

Per tant, no has de compilar amb el gcc, sinó amb el g++ (el compilador de C++).

---

### Post by tanreb20 on 2008-09-19
el problerma papapep és que ni jo recordo d'on el vaig agafar, pero no, no hihavia cap informació de les dependencies, juraria vaja :S:S

Mirare de trobar de on ha sortit, pero sera dificl! jeje

Com és compila amb el g++?

---

### Post by marcoil on 2008-09-19
> **tanreb20 said:**
> Com és compila amb el g++?

Doncs primera, t'has instal·lar el paquet g++, que és el compilador de C++:
```
$ sudo apt-get install g++
```
I després has d'executar la línia que el mateix programa te diu que executis per compilar-lo:

```
$ g++ -Wall pet.cc `pkg-config gtk+-2.0 gdk-pixbuf-xlib-2.0 --cflags` `pkg-config  gtk+-2.0 gdk-pixbuf-xlib-2.0 --libs` -o pet
```

Possiblement te digui que no troba les llibreries necessàries, així que hauràs d'instal·lar també els paquets de desenvolupament que necessita el programa (tret de la línia de compilació):

```
sudo apt-get install libgtk2.0-dev libgdk-pixbuf-dev
```

---

### Post by tanreb20 on 2008-09-19
Ja esta...

Ho he pogut fer al final seguin tls consells que mphas donat!

Ara el problema es q no se com parar aquets animalons!! aarg és orribleXd

---

