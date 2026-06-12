---
title: "Does anyone know how to draw a circuit diagram in LaTeX?"
date: 2010-01-30
forum: Education &amp; Science
---

### Post by YarDYar on 2010-01-30
Hi All,

I'm trying to add a circuit diagram to my LaTeX file. I found a macro library here:
[www.ece.uwaterloo.ca/~aplevich/Circuit_macros/]("http://www.ece.uwaterloo.ca/%7Eaplevich/Circuit_macros/")
which uses a pic interpreter (gpic), and m4 to generate code that LaTeX can interpret (with the help of his circuit_macros) to draw a diagram in the document. 

I'm reading his manual, and got stuck at this step:
> 
If you are using dpic with PSTricks, type the following commands or put them into a script:
```

m4 <path>pstricks.m4 <path>libcct.m4 quick.m4 > quick.pic
dpic -p quick.pic > quick.tex 

```Tikz PGF drawing commands are modified to read pgf.m4 and invoke the
dpic -g option as follows:
```

m4 <path>pgf.m4 <path>libcct.m4 quick.m4 > quick.pic
dpic -g quick.pic > quick.tex 

```If you are using gpic, the commands are
```

m4 <path>libcct.m4 quick.m4 > quick.pic
gpic -t quick.pic > quick.tex 
```pstricks is included in TeXlive, but I don't know where the path for libcct.m4 might be, I can't find any info on the infinet, and Ubuntu file search is super slow. 

Any help would be greatly appreciated.

Thanks a lot.
Yar

---

### Post by Tibuda on 2010-01-30
> **YarDYar said:**
> I'm reading his manual, and got stuck at this step:
pstricks is included in TeXlive, but I don't know where the path for libcct.m4 might be, I can't find any info on the infinet, and Ubuntu file search is super slow. 


this libcct.m4 file is included in the zip/tar.gz available at the footer of that page you linked:

> #  The Circuit_macro distribution:  The complete distribution is available on any CTAN archive in graphics/Circuit_macros. Click  here  to navigate to a CTAN site, or try the latest (possibly unstable) development version,  **zipped  or as a  tar.gz file**. See the Circuit_macros CHANGES file for differences between the development version and the stable CTAN version. 

---

### Post by YarDYar on 2010-02-01
Yeah, all the files were in the tarball that you can download from his site. When I tried running his example, there was a syntax error turning the .pic file to a .tex file, and I didn't know how to fix it. 

I discovered that everything I need is included in the "pst-circ" package, which must be included in my tex install because this tex file gives me EXACTLY what I was looking for.

```

\documentclass[12pt]{article}
 \usepackage{pst-circ}
 \begin{document}
     \begin{pspicture}(11,3)
            \psset{dipolestyle=elektor}
            \pnode(1,2){Vin}\pnode(0.5,2){S}\pnode(0.5,0){Sm}
            \pnode(2.5,2){A}\pnode(4.5,2){B}\pnode(6.5,2){C}
            \pnode(8,2){Cd}\pnode(8.5,2){D}\pnode(9.5,2){E}
            \pnode(2.5,0){Am}\pnode(4.5,0){Bm}\pnode(6.5,0){Cm}
            \pnode(8.5,0){Dm}\pnode(9.5,0){Em}
            \Ucc[labeloffset=0.9](Sm)(S){$V_{in}$}\resistor(Vin)(A){$R$}
            \capacitor(A)(Am){$C_1$} \capacitor(B)(Bm){$C_3$}
            \capacitor[labeloffset=-0.7](D)(Dm){$C_n$}\resistor(E)(Em){$R$}
            \coil(A)(B){$L_2$}\coil(B)(C){$L_4$}
            \wire(Am)(Bm)\wire(Bm)(Cm)\wire(Cm)(Dm)\wire(Dm)(Em)\wire(D)(E)
            \wire(Cd)(D)\psline[linestyle=dashed](C)(Cd)
            \wire(S)(Vin)\wire(Sm)(Am)
            \pscircle *(D){2\pslinewidth} \pscircle *(Dm){2\pslinewidth}
            \pscircle *(A){2\pslinewidth} \pscircle *(Am){2\pslinewidth}
            \pscircle *(B){2\pslinewidth} \pscircle *(Bm){2\pslinewidth}
      \end{pspicture}
 \end{document}

```Whohoo! :) 
Yar!

---

