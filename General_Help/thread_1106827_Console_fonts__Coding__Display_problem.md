---
title: "Console fonts ? Coding ? Display problem"
date: 2009-03-26
forum: General Help
---

### Post by 4rtur on 2009-03-26
Hi,

I have a problem with my console, on each server I have a nice Tux displayed before login. But for some reason it's not displaying correctly on Ubuntu 8.10.

When I connect it shows it like this:

```

     .--.
    |o_o |
    |:_/ |
   //   \\ \\
  (|     | )
 /'\\_   _/`\\
 \\___)=(___/    dufour.monterosa.co.uk

```

but when I ssh from this connection to other server is all ok:

```

     .--.
    |o_o |
    |:_/ |
   //   \ \
  (|     | )
 /'\_   _/`\
 \___)=(___/    castor.monterosa.co.uk

Password: 

```

Is it trying to escape something ?

---

### Post by Vaphell on 2009-03-26
probably, only \'s are messed up. my guess is there are 2 \ in the code
in first example \\ is shown as \\ - that means it is treated like an ordinary string
in second \\ = \ - that means it is treated as an escaped '\'

why results are different is a mystery to me

---

