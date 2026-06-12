---
title: "Beryl Plugin Problem"
date: 2006-12-11
forum: Desktop Environments
---

### Post by Res0dnf7 on 2006-12-11
i have tried to install the new xgl snow plugin for beryl and im having some issues................:
```

-e compiling : snow.c -> build/libsnow.loPackage xrandr was not found in the pkg-config search path.
Perhaps you should add the directory containing `xrandr.pc'
to the PKG_CONFIG_PATH environment variable
Package 'xrandr', required by 'beryl', not found
snow.c:35:36: error: X11/extensions/Xrender.h: No such file or directory
snow.c:37:19: error: beryl.h: No such file or directory
snow.c:95: error: expected specifier-qualifier-list before 'Bool'
snow.c:105: error: expected declaration specifiers or '...' before 'CompWindow'
snow.c:114: error: expected specifier-qualifier-list before 'CompScreen'
snow.c: In function 'snowThink':
snow.c:143: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:143: error: 'SnowScreen' has no member named 's'
snow.c:144: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:145: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:145: error: 'SnowScreen' has no member named 's'
snow.c:146: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:147: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c: In function 'snowMove':
snow.c:157: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:157: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:157: error: 'SnowScreen' has no member named 'lastMsCount'
snow.c:158: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:158: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:158: error: 'SnowScreen' has no member named 'lastMsCount'
snow.c:159: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:159: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:159: error: 'SnowScreen' has no member named 'lastMsCount'
snow.c: In function 'setupDisplayList':
snow.c:198: error: 'SnowScreen' has no member named 'snowTextureLoaded'
snow.c:200: warning: implicit declaration of function 'enableTexture'
snow.c:200: error: 'SnowScreen' has no member named 's'
snow.c:200: error: 'SnowScreen' has no member named 'snowTexture'
snow.c:200: error: 'COMP_TEXTURE_FILTER_GOOD' undeclared (first use in this function)
snow.c:200: error: (Each undeclared identifier is reported only once
snow.c:200: error: for each function it appears in.)
snow.c:203: error: 'SnowScreen' has no member named 'displayList'
snow.c:203: warning: implicit declaration of function 'glGenLists'
snow.c:205: warning: implicit declaration of function 'glNewList'
snow.c:205: error: 'SnowScreen' has no member named 'displayList'
snow.c:205: error: 'GL_COMPILE' undeclared (first use in this function)
snow.c:206: warning: implicit declaration of function 'glBegin'
snow.c:206: error: 'GL_QUADS' undeclared (first use in this function)
snow.c:208: warning: implicit declaration of function 'glTexCoord2f'
snow.c:208: warning: implicit declaration of function 'glVertex2f'
snow.c:209: error: 'SnowScreen' has no member named 'snowTextureSize'
snow.c:210: error: 'SnowScreen' has no member named 'snowTextureSize'
snow.c:210: error: 'SnowScreen' has no member named 'snowTextureSize'
snow.c:211: error: 'SnowScreen' has no member named 'snowTextureSize'
snow.c:213: warning: implicit declaration of function 'glEnd'
snow.c:214: warning: implicit declaration of function 'glEndList'
snow.c:216: error: 'SnowScreen' has no member named 'snowTextureLoaded'
snow.c:218: warning: implicit declaration of function 'disableTexture'
snow.c:218: error: 'SnowScreen' has no member named 's'
snow.c:218: error: 'SnowScreen' has no member named 'snowTexture'
snow.c: At top level:
snow.c:223: error: expected declaration specifiers or '...' before 'CompWindow'
snow.c: In function 'beginRendering':
snow.c:225: error: 'CompScreen' undeclared (first use in this function)
snow.c:225: error: 's' undeclared (first use in this function)
snow.c:225: error: 'w' undeclared (first use in this function)
snow.c:227: warning: implicit declaration of function 'glPushMatrix'
snow.c:228: warning: implicit declaration of function 'glLoadIdentity'
snow.c:229: warning: implicit declaration of function 'glTranslatef'
snow.c:229: error: 'DEFAULT_Z_CAMERA' undeclared (first use in this function)
snow.c:230: warning: implicit declaration of function 'glScalef'
snow.c:233: warning: implicit declaration of function 'glEnable'
snow.c:233: error: 'GL_BLEND' undeclared (first use in this function)
snow.c:234: warning: implicit declaration of function 'glBlendFunc'
snow.c:234: error: 'GL_SRC_ALPHA' undeclared (first use in this function)
snow.c:234: error: 'GL_ONE_MINUS_SRC_ALPHA' undeclared (first use in this function)
snow.c:236: warning: implicit declaration of function 'glTexEnvf'
snow.c:236: error: 'GL_TEXTURE_ENV' undeclared (first use in this function)
snow.c:236: error: 'GL_TEXTURE_ENV_MODE' undeclared (first use in this function)
snow.c:236: error: 'GL_MODULATE' undeclared (first use in this function)
snow.c:238: error: 'SnowScreen' has no member named 'snowTexture'
snow.c:238: error: 'COMP_TEXTURE_FILTER_GOOD' undeclared (first use in this function)
snow.c:239: warning: implicit declaration of function 'glColor4f'
snow.c:245: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:245: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:245: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:246: warning: implicit declaration of function 'glCallList'
snow.c:246: error: 'SnowScreen' has no member named 'displayList'
snow.c:247: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:247: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:247: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:250: error: 'SnowScreen' has no member named 'lastMsCount'
snow.c:251: error: 'SnowScreen' has no member named 'snowTexture'
snow.c:253: error: 'GL_REPLACE' undeclared (first use in this function)
snow.c:254: warning: implicit declaration of function 'glDisable'
snow.c:255: error: 'GL_ONE' undeclared (first use in this function)
snow.c:256: warning: implicit declaration of function 'glPopMatrix'
snow.c: At top level:
snow.c:260: error: expected ')' before '*' token
snow.c:273: error: expected ')' before '*' token
snow.c:304: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'snowPaintScreen'
snow.c:344: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'snowDrawWindow'
snow.c: In function 'InitiateSnowFlake':
snow.c:388: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:388: error: 'SnowScreen' has no member named 's'
snow.c:389: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:390: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:391: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:392: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:393: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c: At top level:
snow.c:396: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'snowInitScreen'
snow.c:433: error: expected ')' before '*' token
snow.c:451: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'snowSetDisplayOption'
snow.c: In function 'snowDisplayInitOptions':
snow.c:530: error: 'CompOption' undeclared (first use in this function)
snow.c:530: error: 'o' undeclared (first use in this function)
snow.c:532: error: 'SnowDisplay' has no member named 'opt'
snow.c:534: warning: implicit declaration of function 'N_'
snow.c:539: error: 'CompOptionTypeFloat' undeclared (first use in this function)
snow.c:545: error: 'SnowDisplay' has no member named 'opt'
snow.c:558: error: 'SnowDisplay' has no member named 'opt'
snow.c:571: error: 'SnowDisplay' has no member named 'opt'
snow.c:584: error: 'SnowDisplay' has no member named 'opt'
snow.c: At top level:
snow.c:625: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
snow.c:642: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'snowInitDisplay'
snow.c:673: error: expected ')' before '*' token
snow.c:683: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'snowInit'
snow.c:695: error: expected ')' before '*' token
snow.c:701: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'snowVTable'
snow.c:725: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/libsnow.lo] Error 1
[PHP][/PHP]
```

thanks for the help in advance!

---

### Post by marc_th on 2006-12-12
[http://ubuntuforums.org/showthread.php?t=316247&highlight=snow]("http://ubuntuforums.org/showthread.php?t=316247&highlight=snow")

---

