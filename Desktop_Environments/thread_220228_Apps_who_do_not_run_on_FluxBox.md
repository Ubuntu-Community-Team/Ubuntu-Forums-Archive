---
title: "Apps who do not run on FluxBox"
date: 2006-07-21
forum: Desktop Environments
---

### Post by WagnerVaz on 2006-07-21
Hi all.
There something wrong, in Gnome i can run firefox and vim without any crash, but when i move to FluxBox it just does not launch. i get the follow message when execute with Aterm:
**For Firefox**
```

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 1339 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

**For Gvim**
```

The program 'vim' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 399 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I Alredy tried run with --sync and it no change.

and in the tail in my /var/log/messages
say something with Gconf o0
[B]The log is in Portuguese Brazil, but someone can grab some information from
there, I think =\[/B]
```

Jul 21 06:34:53 localhost gconfd (wagner-6653): iniciando (versão 2.14.0), pid 6653 usuário 'wagner'
Jul 21 06:34:53 localhost gconfd (wagner-6653): Endereço "xml:readonly:/etc/gconf/gconf.xml.mandatory" resolvido para uma fonte de configuração com permissões apenas de leitura na posição 0
Jul 21 06:34:53 localhost gconfd (wagner-6653): O endereço "xml:readwrite:/home/wagner/.gconf" resolvido para uma fonte de configuração com permissões de escrita na posição 1
Jul 21 06:34:53 localhost gconfd (wagner-6653): Endereço "xml:readonly:/etc/gconf/gconf.xml.defaults" resolvido para uma fonte de configuração com permissões apenas de leitura na posição 2
Jul 21 06:34:53 localhost gconfd (wagner-6653): Endereço "xml:readonly:/var/lib/gconf/debian.defaults" resolvido para uma fonte de configuração com permissões apenas de leitura na posição 3
Jul 21 06:34:53 localhost gconfd (wagner-6653): Endereço "xml:readonly:/var/lib/gconf/defaults" resolvido para uma fonte de configuração com permissões apenas de leitura na posição 4
Jul 21 06:35:23 localhost gconfd (wagner-6653): O servidor GConf não está sendo usado, desligando.
Jul 21 06:35:23 localhost gconfd (wagner-6653): Terminando

```
It says some thing with write and read permitions.

I dunno what is going on. But I hope someone knows how to fix it. =)



**PS:Sorry about my bad english =\**

---

### Post by WagnerVaz on 2006-07-21
no one knows =\ ?

---

### Post by WagnerVaz on 2006-07-21
**Solved!!**
It just crash becouse i told to Fluxbox remember the position and the shade of window, for fix, just clean the content of ~/.fluxbox/apps with:
```

echo "" > ~/.fluxbox/apps

```

Thx :smile:

---

