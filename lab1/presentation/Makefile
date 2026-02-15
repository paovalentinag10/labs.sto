SRC = presentation.md
FILES += $(patsubst %.md, %.pdf, $(wildcard *.md))
FILES += $(patsubst %.md, %.html, $(wildcard *.md))

FILTERS =
PDF_ENGINE =
PDF_OPTIONS =
PDF_FORMAT_OPTIONS = -t beamer --slide-level=2

FILTERS += --citeproc
# FILTERS += -F pandoc-crossref
PDF_ENGINE += --pdf-engine=lualatex
PDF_OPTIONS += --number-sections

REVEALJS_THEME = beige

%.pdf: %.md
	-@pandoc "$<" $(FILTERS) $(PDF_ENGINE) $(PDF_OPTIONS) $(PDF_FORMAT_OPTIONS) -o "$@"

%.html: %.md
	-@pandoc "$<" --embed-resources --standalone -t revealjs -V theme=$(REVEALJS_THEME) -o "$@"

all: $(FILES)
	@echo "=== Перемещение файлов на уровень выше ==="
	@mv -f *.md *.pdf *.docx *.html ../ 2>/dev/null || true
	@echo "=== Удаление PNG файлов ==="
	@rm -f *.png 2>/dev/null || true
	@echo "=== Готово: файлы перемещены, изображения удалены ==="

clean:
	-@rm $(FILES) *~

cleanall: clean
