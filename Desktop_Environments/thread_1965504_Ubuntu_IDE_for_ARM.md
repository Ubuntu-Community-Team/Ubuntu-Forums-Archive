---
title: "Ubuntu IDE for ARM"
date: 2012-04-25
forum: Desktop Environments
---

### Post by jiapei100 on 2012-04-25
Hi, all:

I'm trying to find a flexible IDE for ARM development under Ubuntu 11.10. It looks "gnuarmeclipse" is a good plugin under Eclipse that I can rely on. However, I've got no idea why every time when I tried to build a very simple code
```

#include <stdio.h>

int main(int argc, char** argv)
{
	printf("Error\n");
	return 0;
}

```
I got the following error:
> arm-elf-g++: not found

Does that mean "arm-elf-g++" from [http://www.gnuarm.com](http://www.gnuarm.com) is a must for this plugin "gnuarmeclipse"? Well, actually, besides "arm-elf-g++", I did notice there are some default packages from Ubuntu 11.10 repository, say
> gcc-4.6-arm-linux-gnueabi
cpp-4.6-arm-linux-gnueabi
etc.


I'm just wondering 
1) what's the relationship between "arm-elf-g/arm-elf-g++" and "gcc-4.6-arm-linux-gnueabi/cpp-4.6-arm-linux-gnueabi"?
2) if they can be replaced by each other, is there such an Eclipse plugin, which uses "gcc-4.6-arm-linux-gnueabi/cpp-4.6-arm-linux-gnueabi" to build the ARM projects?

Thank you very much.

Best Regards
Pei

---

