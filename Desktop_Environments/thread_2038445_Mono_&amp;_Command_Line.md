---
title: "Mono &amp; Command Line"
date: 2012-08-06
forum: Desktop Environments
---

### Post by ashkot on 2012-08-06
Hi all,
I am using C# on Mono on Ubuntu and found some code that uses process info class that allows for executing shell commands.

I have an issue where in a command such as 

sudo samtools sort file1.bam  file1.sorted

is executed OK, where as the following command is not.

sudo samtools mpileup -uf ref.fasta file1.sorted.bam | bcftools view -bvcg - > file.bcf

Any ideas??

Thanks,
A

---

### Post by directhex on 2012-08-07
> **ashkot said:**
> Hi all,
I am using C# on Mono on Ubuntu and found some code that uses process info class that allows for executing shell commands.

I have an issue where in a command such as 

sudo samtools sort file1.bam  file1.sorted

is executed OK, where as the following command is not.

sudo samtools mpileup -uf ref.fasta file1.sorted.bam | bcftools view -bvcg - > file.bcf

Any ideas??

Thanks,
A

To understand why this isn't working, you need to understand exactly what it is you're running.

System.Diagnostics.Process allows you to execute a single application, with parameters.

In your first example you're running the application /usr/bin/sudo with the parameters "samtools sort file1.bam  file1.sorted"

The second command, however, you introduce a problem in the form of pipes and redirects. You're trying to use the application /usr/bin/sudo with the parameters "samtools mpileup -uf ref.fasta file1.sorted.bam | bcftools view -bvcg - > file.bcf" but a bunch of that isn't valid as parameters to sudo.

Now, you've got two options here. I haven't tested either, so you'll still need to do some experimenting.

Firstly, consider your pipe and redirect. Whilst they're not valid as far as sudo is concerned, they *are* valid as far as Bash is concerned. So try using Bash as your application, and sudo blah blah as parameters. Might work.

Second option is to manually build the pipes with a second Process object - feed the Process.StandardOutput from the first command into the Process.StandardInput of a second command, and rather than using a file redirect on the command line for the second command's output, use Process.StandardOutput to feed it to a file.

---

