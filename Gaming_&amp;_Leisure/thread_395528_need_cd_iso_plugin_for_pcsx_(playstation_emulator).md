---
title: "need cd iso plugin for pcsx (playstation emulator)"
date: 2007-03-28
forum: Gaming &amp; Leisure
---

### Post by Masterj15 on 2007-03-28
Does anyone know were I can get iso plugin for my playstation emulator. I have cd-r moddy but it does not play iso 9669 (or something like that) Can someone tell me how to turn my isos into a bin or can someone tell me where to get a iso or cd drive plugin for my playstation emulator.

Thanks in advanve:)

---

### Post by Masterj15 on 2007-03-28
bump

---

### Post by hikaricore on 2007-03-28
> **Masterj15 said:**
> Does anyone know were I can get iso plugin for my playstation emulator. I have cd-r moddy but it does not play iso 9669 (or something like that) Can someone tell me how to turn my isos into a bin or can someone tell me where to get a iso or cd drive plugin for my playstation emulator.

Thanks in advanve:)

Here's an easy script I threw together to rip psx cds to bin/toc files.

Open a terminal and type:

```
sudo pico /usr/bin/psxrip
```

Paste the following code:

```

#! /bin/bash
if [ "$1" ]; then
cdrdao read-cd --read-raw --datafile $1 --device /dev/hdd --driver generic-mmc-raw $2;
else
echo ________________________________________
echo ::: Usage - psxrip file.bin file.toc :::
echo
fi

```

Hit ctrl+o to save and then ctrl+x to close pico.

It's not by any means perfect, but it works.

You'll need cdrdao installed for this script to work:

```
sudo apt-get install cdrdao
```

Obviously per my echoed text in the script to rip a cd you'll need to run

```
psxrip filename.bin filename.toc
```

You'll also need to chmod +x the script file for it to run.

```
sudo chmod +x /usr/bin/psxrip
```

Enjoy,


--Aaron

---

### Post by Masterj15 on 2007-03-29
awsome,
thank you :)

---

