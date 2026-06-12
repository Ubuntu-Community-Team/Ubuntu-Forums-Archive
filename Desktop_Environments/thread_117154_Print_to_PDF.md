---
title: "Print to PDF"
date: 2006-01-14
forum: Desktop Environments
---

### Post by jesus_pereira on 2006-01-14
[http://www.linuxval.org/ubuntu/phpBB2/viewtopic.php?t=2991]("http://www.linuxval.org/ubuntu/phpBB2/viewtopic.php?t=2991")

Translation: 
[http://translate.google.com/translate?u=http%3A%2F%2Fwww.linuxval.org%2Fubuntu%2FphpBB2%2Fviewtopic.php%3Ft%3D2991&langpair=pt%7Cen&hl=pt-BR&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.linuxval.org%2Fubuntu%2FphpBB2%2Fviewtopic.php%3Ft%3D2991&langpair=pt%7Cen&hl=pt-BR&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools")

[SIZE="2"][SIZE="1"][SIZE="2"][I]Resume (bad translation):

Adopt the best of the two worlds: Gnome+KDE. Install the KDE packages (better visualization of KDE products on Gnome) and use kprinter to print to pdf on Firefox.

Open Sinaptyc (System > Administration > Synaptic Packages Manager - or - Applications > Add Applications > Advanced > File > Search. Type "kde" and select box "kde"and press "Install" (or similar). It install KDE packages.

You will be able to continue using Gnome as default desktop (...)


In the Firefox, change the print command-line (File > Print > Properties (box "Print Command"): erase lpr -o PreFilter=Level1 ${MOZ_PRINTER_NAME:+"-P$MOZ_PRINTER_NAME"} and write   kprinter .

To produce a pdf-file from Firefox, choose File > Print  and press "Print". On new dialog box, in Printer - Name, choose 'Print to File (PDF)'.

Use KGhostView or Adobe Acrobat Reader; not KPDF or Evince.[/SIZE][/SIZE][/SIZE][/I]

**Impressora de PDF para o firefox**
 
Adote o melhor dos dois mundos Gnome+KDE.  Instale os pacotes do KDE (isto d&#225; uma melhor visualiza&#231;&#227;o dos produtos KDE no Gnome) e utilize o kprinter para imprimir PDF do Firefox.
**Como fazer?**

Primeiro abra o Synaptic (Sistema > Administra&#231;&#227;o > Gerenciador de Pacotes Synaptic - ou - Aplica&#231;&#245;es > Adicionar Aplica&#231;&#245;es > Arquivo > Avan&#231;ado > Procurar ---> digitar     kde      e clicar em "Aplicar", procedendo a instala&#231;&#227;o dos pacotes KDE.

Voc&#234; poder&#225; continuar usando o Gnome como desktop padr&#227;o (e se quiser, fa&#231;a uma limpeza desabilitando os programas menos usados do KDE nos menus, editando os menus (bot&#227;o direito do mouse sobre "Aplica&#231;&#245;es", selecionar: Editar Menus. &#201; s&#243; desbilitar os programas de exibi&#231;&#227;o n&#227;o desejados, desmarcando a respectiva caixa de sele&#231;&#227;o).

Se preferir n&#227;o instalar o KDE todo, instale s&#243; o kprinter - j&#225; li que vi&#225;vel essa op&#231;&#227;o, mas n&#227;o a testei. Preferi instalar o KDE. Tem diversas vantagens que n&#227;o mencionarei aqui e desvantagens como programas com funcionalidades semelhantes, maior ocupa&#231;&#227;o de disco e talvez uma maior demora ao carregar o sistema. Ao instalar s&#243; o kprinter, provavelmente o KDE b&#225;sico ser&#225; tamb&#233;m instalado (Para saber mais, leia [http://www.kubuntu.org/faq.php)](http://www.kubuntu.org/faq.php)).

No Firefox, substituir o comando de impress&#227;o (Arquivo > Imprimir > Propriedades   (caixa comando de Impress&#227;o) por kprinter  ). Antes, copie o comando de impress&#227;o e salve num editor de textos ou anote, para o caso de desejar reverter e voltar a usar o programa de impress&#227;o original.

Pronto. Agora, quando quiser gerar um PDF a partir do Firefox, &#233; s&#243; escolher Arquivo > Imprimir > bot&#227;o "Imprimir" e em Impressora - Nome escolher "Imprimir para Arquivo (PDF).

Aten&#231;&#227;o: o arquivo gerado ser&#225; visto adequadamente no KGhostView ou no Adobe Acrobat Reader. Leitores como o KPDF (e Konqueror) ou o Evince n&#227;o l&#234;em adequadamente os arquivos gerados. Por qu&#234;?  Ainda n&#227;o sei.

---

### Post by bernardfrancois on 2006-01-18
You can print to a file, it wil create a .ps (PostScript file).
After you created it, you open a shell, browse to the directory where you have put the .ps file, and you type:
**ps2pdf *file1*.ps *file2*.pdf**

Offcourse you replace 'file1' with the name of the file you specified, and  'file2' with the name you want to give to your PostScript file.

---

### Post by mattotoole on 2006-01-19
[QUOTE=bernardfrancois]You can print to a file, it wil create a .ps (PostScript file).
After you created it, you open a shell, browse to the directory where you have put the .ps file, and you type:
**ps2pdf *file1*.ps *file2*.pdf**

Offcourse you replace 'file1' with the name of the file you specified, and  'file2' with the name you want to give to your PostScript file.[/QUOTE]

Unfortunately ps2pdf doesn't always work.  For example I often get pages with graphics but no text, etc.

The standard Knoppix distribution comes with a perfectly functioning PDF print driver.  Ubuntu should have this too.

---

### Post by bernardfrancois on 2006-01-20
Are you sure the problem is the ps2pdf command?
Did you check the pdf files before converting?

Maybe it are the settings of the program where you try to print...

Can you tell me exactly what you do to produce the bad pdf file? Then I can try it out here and see if I can find a solution.

---

### Post by kcypers on 2006-01-20
:ks

---

### Post by Bone Down on 2006-01-27
i used the ps2pdf commande on 3 out of 4 files; on the 4th file I received an error.

file 1: ps2pdf 2006.01.06.ps 2006.01.06.pdf (worked)
file 2: ps2pdf 2006.01.13.ps 2006.01.13.pdf (worked)
file 3: ps2pdf 2006.01.20.ps 2006.01.20.pdf (worked)
file 4: ps2pdf 2006.01.27.ps 2006.01.27.pdf (error)

the error:

```
Error: /undefinedfilename in (2006.01.27.ps)
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   --nostringval--   --nostringval--
Dictionary stack:
   --dict:1055/1417(ro)(G)--   --dict:0/20(G)--   --dict:68/200(L)--
Current allocation mode is local
Last OS error: 2
ESP Ghostscript 7.07.1: Unrecoverable error, exit code 1

```
Any ideas on this one?

---

### Post by bernardfrancois on 2006-01-27
Maybe it's a bug in ps2pdf or a ps file which is not following the standards... You could try converting it to another postscript level, or maybe using another command to change it to a pdf file.

Or maybe when creating the ps file, more options might be available for creating the ps file (like choosing between postscript level1 and level2). Choosing different options might solve the problem and make it possible to create the pdf file from it.

Note that you can also try different versions of ps2pdf.

I added you to my msn list, if you want you can send me the ps file and I can try it out.

---

### Post by djgenesis on 2006-01-30
Just a simple question.......
Assume you have a pdf file, that every page is a slide. And i want to put 4 slides in a page and save it as an other pdf file....
Is this possible?
Also , is there a program close to "Adobe Acrobat 6.0 Proffessional" for linux?
thanks

---

### Post by bernardfrancois on 2006-01-30
[QUOTE=djgenesis]Just a simple question.......
Assume you have a pdf file, that every page is a slide. And i want to put 4 slides in a page and save it as an other pdf file....
Is this possible?[/QUOTE]

Maybe there's a tool for that, but there are several ways to do it yourself I think... 
- Try to open the file in open office draw, and print the handouts with 4 slides on one page to a PostScript file. Convert it to pdf.
- Check all possible pdf or postscript viewers if it has an option like what you described.
- Convert the pdf file to a graphics file format (e.g. png, gif), and use (for example) imagemagick to put the images together. Imagemagick offers command-line graphics editing, so you can easily write a bash script to do the trick. Probably the conversion itself can also be done with imagemagick (Hey, maybe I'll try to write a script like that after my exams are finished).
- If you cant find another way, and it's just for one file with few pages, take screenshots of the individual pages and puzzle them together. Lol, I don't think many sane people would try this.

[QUOTE=djgenesis]Also , is there a program close to "Adobe Acrobat 6.0 Proffessional" for linux?
thanks[/QUOTE]
Since you can easily create a pdf file from any program (like lyx, open office), you won't need something like acrobat for creating pdf files. Editing a pdf file is another cup of tea offcourse, I never tried that.

---

### Post by djgenesis on 2006-02-01
[QUOTE=bernardfrancois]Maybe there's a tool for that, but there are several ways to do it yourself I think... 
- Try to open the file in open office draw, and print the handouts with 4 slides on one page to a PostScript file. Convert it to pdf.[/quote]
The file is not supported by office draw :(
> - Check all possible pdf or postscript viewers if it has an option like what you described.
I tried with pdftk as well but no luck 
> - Convert the pdf file to a graphics file format (e.g. png, gif), and use (for example) imagemagick to put the images together. Imagemagick offers command-line graphics editing, so you can easily write a bash script to do the trick. Probably the conversion itself can also be done with imagemagick (Hey, maybe I'll try to write a script like that after my exams are finished).
Bash Script?!?!?! Me?? You must be kidding.. 
I don't even know how to install my drivers properly! it will take me days to finish the script...
> 
- If you cant find another way, and it's just for one file with few pages, take screenshots of the individual pages and puzzle them together. Lol, I don't think many sane people would try this.
LOL

>  Since you can easily create a pdf file from any program (like lyx, open office), you won't need something like acrobat for creating pdf files. Editing a pdf file is another cup of tea offcourse, I never tried that.
This is what i'm talking about..
You see its the details and the ease of use that make windows programs more popular. But instead of using adobe in windows, i will try to make the script myself at some point.

Thanks for your reply

---

### Post by bernardfrancois on 2006-02-02
Ok, I can help you with the script; if you find out which commands to use to do the following things, I'll put it together in a script:
- split the pdf document in multiple files (one for each page) with **pdftk** or try to convert the pdf document to multiple gif/png/... files with imagemagick's **convert** or **mogrify**.
- use imagemagick's **montage** command to put multiple images together (probably you'll first have to resize it using **mogrify**)

[edit]Try to find out first if you can do everything with imagemagick. Probably, that's the case. Then our script will only depend on one other program...[/edit]

Here you can see a quick summary of the command line tools of imagemagick:
[http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)
For more information you can just use **man *toolname***

> 
This is what i'm talking about..
You see its the details and the ease of use that make windows programs more popular. But instead of using adobe in windows, i will try to make the script myself at some point.

In windows it's even more difficult to find free software to edit pdf files.

---

