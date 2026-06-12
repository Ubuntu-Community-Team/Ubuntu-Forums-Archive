---
title: "MSN to Pidgin logs?"
date: 2009-06-11
forum: General Help
---

### Post by rfLarke on 2009-06-11
Hey, I've been trying to merge three years' worth of MSN chatlogs with my pidgin logs, to no avail. I've been converting some other programs' logs successfully, but MSN never works. As yet I've been using Chat Log Converter, but it's new and... pretty buggy. Does anyone know of some other method? I know there's a method of having Pidgin read other program's logs, but I'm looking to outright convert them so I can merge them directly with the log files and have them searchable and indexable by other programs like Beagle.

Thanks, guys!

---

### Post by MestreLion on 2010-09-27
Same problem here...

Actually, i would be happy with a converter from MSN to *ANY* Linux IM. It doesnt matter for me if its Pidgin or aMSN or Empathy, because latter i can easily cross-convert to and from each of them (Pidgin has excelent importers for Empathy, for example)

Bu NONE  of them seems to read the .XML logs from original MSN Live Messenger. 

What you guys suggest? How to convert, and to which IM conversion is better?

Thanks!

---

### Post by Gotty on 2010-12-12
I've written a small php script to convert you're old logs to Pidgin HTML-log files.

You have to execute this script in your "old logs" folder, and it will create a new folder for each contact. Just go in your folder with the terminal, then type "php filename.php", where filename is the php filename.

You need to edit two things : 
- Your usual login (3rd line)
- When I convert dates, I come from a DD/MM/YYYY format (Europe). If you come from a MM/DD/YYYY format (US), you need to change on line 32 [PHP]($mois = $split[1]; $jour = $split[0];)[/PHP] in [PHP]($mois = $split[0]; $jour = $split[1];)[/PHP] (line 32)

Hope it helps !

[PHP]
<?php 

// Your usual login (to use a different color when you're the one talking)
$login="My Login";

if ($dir = opendir("."))
{  
	// Browse all log files, to create folders
	while($file = readdir($dir)) 
	{ 
		$extension=strrchr($file,'.');
		if ($extension==".xml")
		{
			$nom_dossier=ereg_replace("[0-9]|(xml)|(- Archive)|[\.]|[[:blank:]]","",$file);
			$nom_dossier.="@hotmail.com";
			// Create folder for contact		
			if (!file_exists($nom_dossier))
				mkdir($nom_dossier);
		
		
			// Read XML File
			echo $file." has been processed \n";
			$fp = file_get_contents($file);
			$xml = new SimpleXMLElement($fp);
			
			foreach($xml->Message as $message)
			{
				$attributs=$message->attributes();
				$date_message = $attributs['Date'];
					$split = split("/",$date_message); 
					$annee = $split[2]; 
					$mois = $split[1]; 
					$jour = $split[0]; 
					
				$heure=$attributs['Time'];
				$attributs_auteur=$message->From->User->attributes();
				$auteur=$attributs_auteur['FriendlyName'];
			
				$nom_nouveau_fichier=$annee."-".$mois."-".$jour."000000+0100CET.html";
				
				if (!file_exists($nom_dossier."/".$nom_nouveau_fichier))
				{
					// Close previously opened file
					if (isset($newfile))
					{
						$cloture="</body></html>";
						fwrite($newfile,$cloture);
					}
					
					// Create new log file
					$newfile=fopen($nom_dossier."/".$nom_nouveau_fichier, "a+");
					$entree='<html><head><meta http-equiv="content-type" content="text/html; charset=UTF-8"><title>Conversation MSN - Archives</title></head><body><h3>Conversation MSN - Archives</h3><br />';
					fwrite($newfile,$entree);
				} 
				
				else
				
				$newfile=fopen($nom_dossier."/".$nom_nouveau_fichier, "a+");
				$corps_message=str_replace("\r"," ",$message->Text[0]);
				$corps_message=str_replace("\n"," ",$message->Text[0]);
				if ($auteur==$login)
					$color="#16569E";
				else
					$color="#A82F2F";
				$texte='<font color='.$color.'><font size="2">('.$heure.')</font> <b>'.$auteur." : </b></font>".$corps_message."<br />";
				fwrite($newfile,$texte);				

			}
			
		}
	} 
	closedir($dir); 
} 

?>

[/PHP]

---

### Post by jpk.in on 2011-05-13
nice work Gotty...
let me try it

---

