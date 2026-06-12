---
title: "Using List or verbose flag output within a conditional."
date: 2009-07-29
forum: Desktop Environments
---

### Post by Dmritard96 on 2009-07-29
Hi all,
I have never really done much with bash and I am unsure of how to use verbose output as conditional parameter.  For example, I have a laptop and I have recently started using disper (wonderful btw) and I want a script that will toggle between dual screen and single screen.  I use the same secondary screen so was thinking I could use the "list" option in the program and compare it to what I see when I do it in the shell.

For Example:
```

#!/bin/bash
if [disper -l "display DFP-0: AUO
 resolutions: 320x240, 400x300, 512x384, 576x432, 680x384, 640x480, 720x450, 640x512, 700x525, 800x512, 840x525, 800x600, 960x540, 960x600, 1024x768, 1152x864, 1360x768, 1440x900
display DFP-1: Envision EN9110
 resolutions: 320x175, 320x200, 360x200, 320x240, 400x300, 416x312, 512x384, 640x350, 576x432, 640x400, 680x384, 720x400, 640x480, 720x450, 640x512, 700x525, 800x512, 840x525, 800x600, 960x540, 832x624, 960x600, 896x672, 928x696, 1024x768, 1152x864, 1280x960, 1280x1024"
]
then
  disper -e -t left

elif 
  disper -s
fi

```

Im sure that I need to pipe it but I really don't know much unix...Any help would be greatly appreciated

Cheers

---

### Post by Dmritard96 on 2009-07-29
Solved!
```

#!/bin/bash
disper -l = list
output = "display DFP-0: AUO
 resolutions: 320x240, 400x300, 512x384, 576x432, 680x384, 640x480, 720x450, 640x512, 700x525, 800x512, 840x525, 800x600, 960x540, 960x600, 1024x768, 1152x864, 1360x768, 1440x900
display DFP-1: Envision EN9110
 resolutions: 320x175, 320x200, 360x200, 320x240, 400x300, 416x312, 512x384, 640x350, 576x432, 640x400, 680x384, 720x400, 640x480, 720x450, 640x512, 700x525, 800x512, 840x525, 800x600, 960x540, 832x624, 960x600, 896x672, 928x696, 1024x768, 1152x864, 1280x960, 1280x1024"
if [$list = $output]
then
  disper -e -t left
  echo dual
else
  disper -s
  echo single
fi

```

While this works easily enough...it seems unnecessary to use these variables any advice?
Also, is there a way to have this script run when the moniter is detected?
Cheers

---

