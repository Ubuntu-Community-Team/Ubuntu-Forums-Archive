---
title: "Bash-remove characters from lines"
date: 2009-05-15
forum: General Help
---

### Post by daveli on 2009-05-15
Hi list!
I am a beginner for linux and bash, but I have a task I would like to perform on a text file. 
The file has names and code numbers, like the following

Patrick J Murray
atmn91722346np990
Anne W Tompson
zqtt33087765ac591
.
.

And I want to remove the first four characters from the code, but this only happens on every other line.

I have found out that ${string:4} would do the trick for one single variable and I  guess I have to do everything in a loop selecting even lines, with something like:
do
   out=$(( $n % 2 ))
   if [ $out eq 0 ]
   then
    <<Remove the characters>>
    let n=$n+1
   fi
done

but how do I put this together for my file?

thanks ever so much for your help

D.

---

### Post by geekua on 2009-05-15
You may use sed
```
sed 'n;s/^.\{4\}//' input.file > output.file
```to remove first four symbols for every second line
or
```
sed '/[0-9]/s/^.\{4\}//' input.file > output.file
```to remove first four symbols for lines which contain digits

---

### Post by daveli on 2009-05-15
Thanks Geekua, I wasn't aware of sed. That works just fine for one file!
Can I actually include that sed command in a bash script or a loop to do the task for everyfile in a directory at the same time, or are they incompatible?? I guess I can type the sed command for every file at a time, but I am trying to make things automatic.

I am not very sure about the difference or the relation between sed and bash, is sed a bash command? I am a bit confused!

TIA

D.

---

### Post by hal10000 on 2009-05-15
You can use the sed command in shell scripts to make them work as you want. sed is a very powerful command for manipulation of text files. If you often have to do such tasks, it would be a good idea to learn something about the sed command ([COLOR="Red"]man sed[/COLOR] or [COLOR="Red"]info sed[/COLOR]) or find help in the internet (e.g. at [http://tldp.org/LDP/Bash-Beginners-Guide/html/chap_05.html]("http://tldp.org/LDP/Bash-Beginners-Guide/html/chap_05.html")).
You could also use the awk command for extended manipulation of text files ([http://tldp.org/LDP/Bash-Beginners-Guide/html/chap_06.html]("http://tldp.org/LDP/Bash-Beginners-Guide/html/chap_06.html"))

---

