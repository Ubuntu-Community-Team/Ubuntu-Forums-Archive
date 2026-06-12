---
title: "Compiz Fusion + WINE"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by Jeremiah Griffin on 2007-11-22
Recently I got off my lazy ****, fixed the drivers for my graphics card (NVIDIA GeForce2 MX/MX-400 AGP), and installed Compiz Fusion. But I've also become addicted to the late twentieth century game, Star Wars: The Phantom Menace. Of course, this only runs in WINE. Sadly, when Compiz Fusion is running, WINE only renders a black screen no matter if virtual desktops are enabled or not (and they must be in order to play TPM). Clearly I'm torn between the productivity boost that I get when using Compiz Fusion and having some playful downtime.

My NVIDIA drivers were installed via Envy.

Is there any way to fix this?

---

### Post by aatiis on 2007-11-24
Hi. I read something similar in another thread... Can't remember where. They suggested you disable Compiz while playing :( Actually (as they say) the problem is not with Compiz, but with Xgl. They say a ```
metacity --replace
``` would fix it.
I was using Gnome a while, but I switched back to good old KDE, so I can only say that a ```
kwin --replace
``` won't fix the problem.
I know, it's not a fix, it's a workaround. If it even works. Sorry if I didn't help much...

---

### Post by Jeremiah Griffin on 2007-11-25
Thanks...I put this hack-up workaround together a day ago. It works, but it's annoying. :P

```
/**
 * winexgl
 * By Jeremiah Griffin <jeremiahzg@gmail.com>
 */

#include <stdio.h>
#include <string.h>

#define ETC_WINEXGL "/usr/local/etc/winexgl"
#define CMD_SIZE 1024

int main(int argc, char *argv[])
{
	char cmd[CMD_SIZE];
	
	printf("winexgl\n");
	printf("By Jeremiah Griffin <jeremiahzg@gmail.com>\n\n");
	
	if (argc < 2) {
		printf("usage: %s params\n", argv[0]);
		printf("\tparams are a single string passed to wine\n", argv[0]);
		return 0;
	}
	
	FILE *fp;
	fp = fopen(ETC_WINEXGL, "r");
	if (fp == NULL) {
		printf("%s: error: %s could not be found!\n", argv[0],
		       ETC_WINEXGL);
		return 0;
	}
	fgets(cmd, CMD_SIZE, fp);
	fclose(fp);	
	system(cmd);
	
	sprintf(cmd, "wine %s", argv[1]);
	system(cmd);
	
	system("compiz &");
	
	return 0;
}
```

Example /usr/local/etc/winexgl:
```
metacity --replace &
```

Building & installing:
```
gcc winexgl.c -o winexgl
sudo cp winexgl /usr/local/bin
```

- Jeremiah

---

