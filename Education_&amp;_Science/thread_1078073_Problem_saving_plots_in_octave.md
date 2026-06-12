---
title: "Problem saving plots in octave"
date: 2009-02-22
forum: Education &amp; Science
---

### Post by snakep on 2009-02-22
Hello,

I am trying to save a plot in octave.  I can save it just fine, but I want to modify the font size and resolution.  I have tried 

```
print('alg2.png','-F:20');
```

but nothing happens.  The font size does not change.  I have also tried changing the font size when I plot:

```
ylabel('y','FontSize',18);
``` 

But this results in an error:

```
warning: set: invalid property `FontSize'
```

I have found suggestions to run commands something like "gset terminal" followed by "replot", but these all return parse errors.  BTW, I am running octave 2.9.12.

---

### Post by Xnst on 2009-02-24
Hi snakep,

I think the main problem with fonts and octave in ubuntu is that helvetica is not present, or present in a way it should be. Therefore, I direct octave to use Vera instead. So my suggestion is to direct gdconf to Vera with:

```

export GDFONTPATH="/usr/share/fonts/truetype/ttf-bitstream-vera"
export GNUPLOT_DEFAULT_GDFONT="Vera.ttf"

```
in the ~/.bash_profile or similar. The last line does not seem to work for me so I have to hard code the use of Vera. Once you have logged in again you should be able to control font sizes and names with lines like the ones below. 

```

xlabel('strain (%)','FontName','Vera','FontSize',14)
ylabel('stress  (MPa)','FontName','Vera','FontSize',14)

```

I think there is more work possible to control the size of the numbering on the axes, but so far I have not been needing that. If you find a way please post it here.

Also, some font related stuff and octave have been discussed in thread 


[http://ubuntuforums.org/showthread.php?t=428496]("http://ubuntuforums.org/showthread.php?t=428496")

perhaps you will find additional info there.

---

