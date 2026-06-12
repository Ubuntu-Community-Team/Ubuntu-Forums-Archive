---
title: "editing a text file automatically"
date: 2019-04-29
forum: Education &amp; Science
---

### Post by Lewis Arthurton on 2019-04-29
Hello Ubuntu Folks 

I am looking to edit a text file using sed or whatever method works to make the following changes:

Original: 
```
Chromosome      ena     CDS     153     1535    .       +       0       transcript_name "transcript:AAS13770";  gene_id "gene:WD_0001"; gene_name "dnaA";
Chromosome      ena     exon    3028    3115    .       +       .       transcript_name "transcript:WD_tRNA-Leu-1-1"; gene_id "gene:WD_tRNA-Leu-1"; gene_name "WD_tRNA-Leu-1"; 
```

New: 
```
Chromosome      ena     CDS     153     1535    .       +       0       **transcript_id "transcript:AAS13770";** transcript_name "transcript:AAS13770"; gene_id "gene:WD_0001"; gene_name "dnaA";
Chromosome      ena     exon    3028    3115    .       +       .       **transcript id transcript:WD_tRNA-Leu-1-1"; **transcript_name "transcript:WD_tRNA-Leu-1-1"; gene_id "gene:WD_tRNA-Leu-1"; gene_name "WD_tRNA-Leu-1"; 
```

Essentially I would like to take the transcript_name ("transcript:AAS13770"), add a new field before with transcript_id and paste the transcript name after this ending with a semi colon and continue this for every line. 

Does anyone have any idea how to do this? I'm looking at sed but I cannot get my head around it. sorry to be a pain.

Best wishes,

Lewis

---

### Post by spjackson on 2019-04-30
This command seems to do what you describe:
```

sed 's/\(transcript_name[^"]*\)\("[^"]*"\)/transcript_id \2; \1\2/' transcript.in

```
When you are confident that it is doing what you want, you can update the file by using the --in-place option:
```

sed --in-place 's/\(transcript_name[^"]*\)\("[^"]*"\)/transcript_id \2; \1\2/' transcript.in

```
Here's a short explanation in case you need to tweak the expressions a bit.

[LIST]
[*]The first set of capture parentheses \(\) match transcript_name plus any following characters up to but not including the first double-quote.
[*]This is assigned to the \1 variable.
[*]The second set of capture parentheses match everything between the following double-quote and its closing double-quote, including the enclosing double-quotes.
[*]This is assigned to the \2 variable.
[*]Replace all that (\1 followed by \2) with /transcript_id \2; \1\2/ which I hope is self-explanatory given the above.
[/LIST]

---

### Post by xadder on 2019-05-14
Just to suggest additional methods, good-old fashioned 'awk' can do this quite well too:

    awk '{print $1, $2, $3, $4, $5, 6, $7, $8, " transcript_id", $10, $9, $11, $12, $13, $14}' in.txt > out.txt

where $1 means first field, etc. Actually I think a python script would be clearer for any long-term usage, using 'split()' to read the fields, but it depends how much work you want to do.

---

### Post by spjackson on 2019-05-14
> **xadder said:**
> Just to suggest additional methods, good-old fashioned 'awk' can do this quite well too:

    awk '{print $1, $2, $3, $4, $5, 6, $7, $8, " transcript_id", $10, $9, $11, $12, $13, $14}' in.txt > out.txt

where $1 means first field, etc. Actually I think a python script would be clearer for any long-term usage, using 'split()' to read the fields, but it depends how much work you want to do.

$10 needs repeating after $9 as well as appearing before it, but otherwise, this may suffice. This awk solution assumes that it is OK to reduce all the spaces between fields to a single space. That may be OK, I don't know. It also assumes that there are no spaces within the double-quoted fields. This is true for the example given but may not be true more generally, I don't know.

The sed solution given above transposes the input given by the OP to the exact example output given and would work if any double-quoted fields contained spaces (but not escaped double-quotes).

---

