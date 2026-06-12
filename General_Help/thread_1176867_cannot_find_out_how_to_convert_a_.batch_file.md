---
title: "cannot find out how to convert a .batch file"
date: 2009-06-02
forum: General Help
---

### Post by matt12345 on 2009-06-02
Hi, I'm pretty new to ubuntu. I got this to work on another type of server but does not work on this one. would anyone mind converting this .bat file so it is compatible?

```
@echo off

Title PvP Planet Client V2

cd ./ClientFiles/

echo Welcome to PvP Planet!

echo Please visit the forums at: Www.Jinrake.Com

Start JAVAW -Xmx400m -cp .;Theme.jar Gui 0 0 lowmem members 32

pause

```

---

### Post by Ocxic on 2009-06-02
#!/bin/bash

#Title PvP Planet Client V2

cd ./ClientFiles/

echo "Welcome to PvP Planet!"

echo "Please visit the forums at: Www.Jinrake.Com"

Start JAVAW -Xmx400m -cp .;Theme.jar Gui 0 0 lowmem members 32  <-- i dunno what this is suppose to do

---

### Post by matt12345 on 2009-06-03
would i put this in a .sh file?

---

### Post by slurdge on 2009-06-03
yes.

then
```
chmod +x yourfile.sh
./yourfile.sh
```

and it should work

---

### Post by matt12345 on 2009-06-04
uhhhg i get this when i try to run it in terminal D:

```
matthew@matthew-desktop:~/Desktop/pvp$ chmod +x launch.sh
matthew@matthew-desktop:~/Desktop/pvp$ ./launch.sh
invalid file (bad magic number): Exec format error
matthew@matthew-desktop:~/Desktop/pvp$ 




```

---

### Post by munky99999 on 2009-06-04
> **matt12345 said:**
> uhhhg i get this when i try to run it in terminal D:

```
matthew@matthew-desktop:~/Desktop/pvp$ chmod +x launch.sh
matthew@matthew-desktop:~/Desktop/pvp$ ./launch.sh
invalid file (bad magic number): Exec format error
matthew@matthew-desktop:~/Desktop/pvp$ 

```

I'm thinking that it's trying to goto cd ./ClientFiles/ which doesnt exist? Giving that error?

Or that last line isnt doing it right. Whatever it's supposed to do... you got me.

---

### Post by matt12345 on 2009-06-05
im still getting the same error :(

---

### Post by bacardiandwatermelon on 2009-06-05
I'd use the hash to find out which line is causing it to bail...

---

### Post by matt12345 on 2009-06-05
and witch wuld that be?

---

### Post by matt12345 on 2009-06-06
come on guys atleast try to help me :(

I don't mean to be picky but I really need this up.

---

### Post by sneaky_zekey on 2010-08-19
so i also need a .bat converted/rewritten i am slowing understanding how to do it but not fast enough,any suggestion is basicly a script bat that ports android theme to an updated rom by copying images from old rom to new rom


```
@echo off 
mode con:cols=61 lines=40 
IF NOT EXIST "%~dp0old\app" mkdir old\app 
IF NOT EXIST "%~dp0old\framework" mkdir old\framework 
IF NOT EXIST "%~dp0new\app" mkdir new\app 
IF NOT EXIST "%~dp0new\framework" mkdir new\framework 
echo Welcome To Theme Porter 
echo ----------------------- 
set dcrt=app 
:restart 
echo. 
if (%dcrt%)==(app) ( 
echo Tranferring Apps 
) 
if (%dcrt%)==(framework) ( 
echo Tranferring Framework 
) 
echo ----------------------- 
echo. 
rem Getting apk name 
FOR %%F IN ("%~dp0old\%dcrt%\*.apk") DO ( 
    rem Check if corresponding apk exists in new rom 
    if EXIST "%~dp0new\%dcrt%\%%~nF%%~xF" ( 
        cd tools 
        rem Extract apk's pngs 
        echo %%~nF 
        7za x -o"../old/%dcrt%/%%~nF" "../old/%dcrt%/%%~nF%%~xF" *.png -r > nul 
        7za x -o"../new/%dcrt%/%%~nF" "../new/%dcrt%/%%~nF%%~xF" *.png -r > nul 
        cd .. 
        IF EXIST "%~dp0old\%dcrt%\%%~nF" ( 
            rem Getting folder name 
            FOR /F %%E IN ('dir "%~dp0old\%dcrt%\%%~nF\res\*" /A:D /S /B') DO ( 
                rem Getting png name 
                FOR %%G IN ("%~dp0old\%dcrt%\%%~nF\res\%%~nE\*.png") DO ( 
                    rem Check if same png exists in the rom ur trying to theme 
                    IF NOT EXIST "%~dp0new\%dcrt%\%%~nF\res\%%~nE\%%~nG%%~xG" ( 
                    del /Q "%~dp0old\%dcrt%\%%~nF\res\%%~nE\%%~nG%%~xG" 
                    ) 
                ) 
            ) 
            cd tools 
            7za a -tzip "../new/%dcrt%/%%~nF%%~xF" "../old/%dcrt%/%%~nF/*" -mx9 *.png -r > nul 
            cd .. 
            rmdir /S /Q "%~dp0old\%dcrt%\%%~nF" 
            rmdir /S /Q "%~dp0new\%dcrt%\%%~nF" 
        ) 
 
    ) 
) 
if (%dcrt%)==(app) ( 
set dcrt=framework 
goto restart 
) 
echo. 
echo Done 
:dione 
ping 127.0.0.1 -n 5 -w 500 > tools\nul  
del /Q tools\NULL
```

---

