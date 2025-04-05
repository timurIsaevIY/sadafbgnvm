# Генерация изображений в стиле Альбрехта Дюрера с помощью Stable Diffusion

## 📌 Идея проекта

Цель проекта — обучить генеративную нейросеть Stable Diffusion для создания новых изображений в стиле немецкого художника-графика Альбрехта Дюрера. Мы стремились получить гравюроподобные изображения, в которых прослеживаются характерные особенности манеры Дюрера: чёткая штриховка, контраст, детализация и анатомическая точность.

---

## 📁 Исходный датасет

Для обучения был собран датасет из **170 изображений** оригинальных работ Альбрехта Дюрера. Изображения:

- приведены к **квадратному формату (1:1)** путём добавления белых рамок;
- охватывают как его известные гравюры (например, *Меланхолия I*, *Адам и Ева*), так и менее известные офорты, рисунки и эскизы;
- сохранены как в виде `.parquet`-датасета, так и в виде обычных изображений в папке `dataset/`.

📌 Ссылка на датасет (репозиторий): [anyuta0001/Durer](https://huggingface.co/datasets/anyuta0001/Durer)

<h3>📜 Примеры изображений из датасета</h3>

<div align="center" style="display: flex; flex-wrap: wrap; gap: 10px; justify-content: center;">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/001-FWrU5Cwtk5M.jpg" width="220">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/002-2KTXQUCZB8w.jpg" width="220">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/011-sWj7uKnnIVM.jpg" width="220">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/007-jLaRtDbWhTQ.jpg" width="220">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/009-yd41-lpzM6w.jpg" width="220">
</div>


---

## 🛠️ Обучение модели

Для обучения использовалась методика **LoRA DreamBooth** на базе модели `stabilityai/stable-diffusion-xl-base-1.0`.

**Параметры обучения:**
- `max_train_steps=200`
- `train_batch_size=1`
- `fp16`, `8bit Adam`, `gradient_checkpointing` — для экономии памяти


[![Обученная модель](https://img.shields.io/badge/HuggingFace-Модель-ffcc00?logo=huggingface&logoColor=black)](https://huggingface.co/anyuta0001/durer_style_LoRA)


📓 Ноутбук с обучением: [durer.ipynb](./durer.ipynb)

---

## 🧠 Результат генерации

После обучения модель научилась воссоздавать изображения в гравюрной технике. Ниже приведены некоторые **сгенерированных изображений**:

<h3>📜 Сгенерированные изображения в стиле Альбрехта Дюрера</h3>

<div align="center" style="display: flex; flex-wrap: wrap; gap: 10px; justify-content: center;">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_00.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_01.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_02.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_03.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_04.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_05.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_06.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_07.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_08.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_09.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_10.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_11.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_12.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_13.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_14.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_15.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_16.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_17.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_18.jpg" width="320">
  <img src="https://huggingface.co/datasets/anyuta0001/Durer/resolve/main/generated/durer_gen_19.jpg" width="320">
</div>


🖼️ Все изображения чёрно-белые, с насыщенной штриховкой и выразительными силуэтами.

---

## 🧾 Анализ и комментарии

- **Манера исполнения**: Модель успешно переняла гравюрную технику — чёткие линии, параллельную/перекрёстную штриховку.
- **Анатомия и композиция**: Хотя иногда наблюдаются неточности, общая композиция и дух работ Дюрера сохраняется.
- **Передача света и тени**: Используется классическая игра контрастов, где белый фон выделяет чёрную штриховку.
- **Вариативность**: В зависимости от промпта появляются разные композиционные решения и сюжетные ходы.

---

## 💬 Использование ИИ

Помимо обученной модели, для генерации промптов и написания пояснений использовалась модель **ChatGPT**:

- Для генерации текстовых описаний (промптов).

---

## 📓 Содержимое проекта

- `durer.ipynb` — ноутбук с обучением и генерацией изображений
- `dataset/` — папка с исходными изображениями для обучения
- `generated/` — сгенерированные изображения после обучения
- `README.md` — описание проекта

---
