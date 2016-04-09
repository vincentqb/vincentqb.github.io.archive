#Edit, Compile, Convert and Show the LaTeX File with either PDFLatex or Latex
FILE1=example

#TYPE is ps or pdf
TYPE=ps 

#Run sequence of commands ending in the display of latex file
build: compile-$(TYPE) convert-$(TYPE) show
bibuild: bib-$(TYPE) build
rebuild: clean build
rebibuild: clean bibuild
all: matlab build
clean:
	rm -f *.bak *.aux *.log *.bbl *.blg *.toc *.lof *.lot *.out $(FILE1).dvi $(FILE1).ps $(FILE1).pdf

#Commands to bibtex, compile pdf/latex files, convert to pdf
compile-ps: 
	latex $(FILE1).tex && latex $(FILE1).tex
compile-pdf:
	pdflatex $(FILE1).tex && pdflatex $(FILE1).tex
convert-ps:
	dvips $(FILE1).dvi -t letter -Ppdf \
	&& ps2pdf -sPAPERSIZE=letter -dOptimize=true -dEmbedAllFonts=true -dUseFlateCompression=true $(FILE1).ps
convert-pdf:
	true #Already a PDF...
bib-ps: 
	latex $(FILE1).tex && bibtex $(FILE1)
bib-pdf: 
	pdflatex $(FILE1).tex && bibtex $(FILE1) 
show: 
	evince -p 1 $(FILE1).pdf &
