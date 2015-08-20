# My-Scripts-NGS
module avail	# opens up list of all the names of the softwares in the HPC

# the following is a list of software modules to load; OKCHPC (COWBOY) 
module load fastqc/0.10.1 		# loads the Fastqc software
module load trimmomatic/0.27		# trimming the reads
module load trinity/r20140413p1		# generating the transscriptome assembly
module load  blast+/2.2.30		# loads the blast+ software for blasting the assembled 						reads
module load khmer/0.4			# Jellyfish and Khmer: Quality Assesment to analyze the 					trimmed read

# Assesing the read quality for the FastQ files using Fastqc
#the following is the list of commands to run the softwares
ls	# shows you the file in the directory
mkdir YOSharmi 	# makes a new directory for the YOfastQ files
cd YOSharmi	# takes to the YOSharmi directory
curl -O ftp://ftp.genome.ou.edu/pub/for_Durica/YO_dir/YO_1_Baseline_R1.fastq.gz		# gets the file from the YO illumina website and downloads in your HPC
less YO_1_Baseline_R1.fastq.gz 		 # Shows me the mode of fastQ files  

#output of a fastQ file
@ACB053:88:C29N0ACXX:2:1101:1174:2155 1:N:0:ATCACG
GGAGGACCACGAACGGAGGAAGAGGGACACGATTGTCTCCGGAGGGGTTGATCACCAGGTGAATCCCAACGGCAACTCCATTGGTGCCTCTGCCACTTTG
+
???BD:22ADDDDEI@+?:?D)?C;:)?BB??D=6B)8))54548'3,,,-5-55(,((5:(,5:4>>A>0&)&023+(+(((4:>(+44444+:AAAA(
@ACB053:88:C29N0ACXX:2:1101:1211:2159 1:N:0:ATCACG
ATAAAGTATGTGAAGGTATCAGGGTATTTTAATTATGCAAACAATGGTAACCAAGTATTTTAATTGTGTAAACAATAGCATGAGAGTATTTTAATCAAGT
+
?=?DDBADFFDDDGG3<AICEBF>FC@HHB43CFFEG>?F<F)?*9BBDBBD@FH99B<4B<BGGIFA==BCE).=7;@@


md5sum YO_1_Baseline_R1.fastq.gz	# checks if my files are preserved
gunzip YO_1_Baseline_R1.fastq.gz	# unzips all the .gz files
zcat YO_1_Baseline_R1.fastq.gz | head	# unzips only the fisrt few files as it is piped to head

fastqc ./YO_1_Baseline_R1.fastq.gz 	# analyzes you FastQ files
cd YO_1_Baseline_R1_fastqc		# go to the fastqc file
cat summary.txt				# summary of the fastqc files
cp -r YO_1_Baseline_R1_fastqc ~/


#screen
screen # opens a interface to work on the HPC even when the connection is lost

Ctrl A+D # detach from the screen and carry out other program and your last job keeps running in the screen

screen -r # goes back to the running screen

exit # exits the screen
