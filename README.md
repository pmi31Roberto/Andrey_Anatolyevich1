# Лабораторная работа(2). Создание системы автоматического исправления опечаток в тексте.

Этот проект представляет собой простой автокорректор для исправления опечаток в тексте на различных языках, написанный на Python.


## Основные особенности проекта:

1. **Автокоррекция:**
   - Код предоставляет класс `Speller`, который автоматически исправляет опечатки в словах и предложениях.

2. **Загрузка данных:**
   - Функционал загрузки данных из tar-архивов, содержащих информацию о частоте встречаемости слов в языке.

3. **Поддержка разных языков:**
   - Проект разработан с учетом поддержки различных языков. Добавление новых языков - простая задача.

4. **Прогресс загрузки:**
   - Используется класс `ProgressBar` для отображения прогресса загрузки данных в виде ASCII-графики.

5. **Обработка ошибок и резервные источники:**
   - Обработка ошибок при загрузке данных. При отсутствии данных пытается загрузить из нескольких источников.

6. **Обратная совместимость:**
   - Класс `LazySpeller` обеспечивает обратную совместимость для использования старого способа вызова автокорректора.

7. **Гибкость настройки:**
   - Параметры класса `Speller` позволяют настраивать порог частоты слова, использовать быстрый метод коррекции и ограничивать замены.


## Как использовать

### Установка

Сначала убедитесь, что у вас установлен Python. Затем склонируйте репозиторий:

```bash
git clone https://github.com/your-username/autocorrect.git
cd autocorrect
```
## Перейдите в каталог проекта:
cd autocorrect

## Установите зависимости:
```bash
pip install -r requirements.txt
```

## Использование

Пример использования:

```python
## Пример использования с опечаткой

```python
from autocorrect import Speller

spell_checker = Speller(lang='en')
input_sentence = "Thiss is an example sentence with a typppo."
corrected_sentence = spell_checker.autocorrect_sentence(input_sentence)

print(f"Input: {input_sentence}")
print(f"Output: {corrected_sentence}")

```
```
Input: Thiss is an example sentence with a typppo.
Output: This is an example sentence with a typo.
```
### Использование через командную строку
1. **Запустите скрипт autocorrect_cli.py с указанием языка и предложения:**
   ```
   python autocorrect_cli.py --lang ru --sentence "Превед, медвед!"
   ```
   Результат:
   ```
   Перед, медвед!
   ```
## Пример1: Расширенные настройки параметров

```python
from autocorrect import Speller

# Создаем экземпляр класса Speller с расширенными параметрами
spell_checker = Speller(lang='en', frequency_threshold=0.1, fast_correction=True, max_replacements=3)

# Пример использования с опечаткой и расширенными настройками
input_sentence = "Thiss is an example sentence with a lot of typppos."
corrected_sentence = spell_checker.autocorrect_sentence(input_sentence)

print(f"Input: {input_sentence}")
print(f"Output: {corrected_sentence}")
```
#Вывод
```
Input: Thiss is an example sentence with a lot of typppos.
Output: This is an example sentence with a typo.
```
## Пример: Добавление поддержки нового языка
```
from autocorrect import Speller

# Создаем экземпляр класса Speller с добавлением нового языка
spell_checker = Speller(lang='es')

# Пример использования с опечаткой на испанском языке
input_sentence = "Esto es un ejemplo de oración con un errror."
corrected_sentence = spell_checker.autocorrect_sentence(input_sentence)

print(f"Input: {input_sentence}")
print(f"Output: {corrected_sentence}")
```
#Вывод
```
Input: Esto es un ejemplo de oración con un errror.
Output: Esto es un ejemplo de oración con un error.
```
