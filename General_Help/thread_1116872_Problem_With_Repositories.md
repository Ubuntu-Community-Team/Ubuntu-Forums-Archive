---
title: "Problem With Repositories"
date: 2009-04-05
forum: General Help
---

### Post by Cresar on 2009-04-05
Well, my problem is with the repositories that every time I try to update the synaptic package and an update check and I get this other error in these repositories ....
What is the solution? and the problem or root?
Or eliminate these repositories ago?
[B]
Error:[/B]

```
Error de GPG: http://ppa.launchpad.net intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 28A8205077558DD0Error de GPG: http://ppa.launchpad.net intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 9BDB3D89CE49EC21Imposible obtener http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/intrepid/deb-src/binary-i386/Packages.gz  404 Not Found
Imposible obtener http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/intrepid/http://ppa.launchpad.net/do-core/ppa/ubuntu/binary-i386/Packages.gz  404 Not Found
Imposible obtener http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/intrepid/intrepid/binary-i386/Packages.gz  404 Not Found
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
```

---

### Post by taurus on 2009-04-05
Looks like you need to install PGP key for ppa.launchpad.net.

[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA)
[http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743)

---

### Post by mb_webguy on 2009-04-05
Copy and paste the following into the terminal.```
gpg --keyserver keyserver.ubuntu.com --recv 28A8205077558DD0
gpg --export --armor 28A8205077558DD0 | sudo apt-key add -

```After that, you should no longer get those error messages (or at least the first).

---

