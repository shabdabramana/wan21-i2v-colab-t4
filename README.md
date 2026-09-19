# Wan 2.1 I2V — Google Colab (free T4)

Рабочий ноутбук для генерации видео из фото через Wan 2.1 (image-to-video, 14B) на бесплатном тарифе Colab (GPU T4 16 ГБ).

## Используемый стек
- ComfyUI v0.36.0 + плагин `ComfyUI-GGUF` (city96)
- Wan 2.1 I2V 14B 480P в кванте GGUF **Q4_K_M** (`city96/Wan2.1-I2V-14B-480P-gguf`)
- Текстовый энкодер UMT5-XXL в кванте GGUF Q4 (`city96/umt5-xxl-encoder-gguf`) — экономит ~12.7 ГБ ОЗУ
- VAE: `Comfy-Org/Wan_2.1_ComfyUI_repackaged`
- Апскейл финального видео: Real-ESRGAN x4plus (1080p/720p)

## Запуск в один клик
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/shabdabramana/wan21-i2v-colab-t4/blob/main/wan21_i2v_colab_t4_v2.ipynb)

1. **Runtime → Change runtime type → GPU T4 → Save**
2. **Runtime → Run all**
3. Первый запуск качает модели (~17 ГБ, 10–40 мин) — потерпите, повторные запуски уже без этого.

## Параметры по умолчанию
- Разрешение диффузии: 832×480 (нативный)
- Длина: 81 кадр (≈5 с на 16 fps)
- Шагов: 20, CFG: 6.0, sampler `uni_pc`/`simple`, ModelSamplingSD3 shift=8.0

## Особенности
- Адаптивный граф: автоматически определяет формат `SaveVideo` (новый `video` / старый `images`) по версии ComfyUI
- Идемпотентная установка: повторный Run all докачивает недостающее и не качает заново
- Опционально: сохранение моделей на Google Drive (одноразово) и восстановление оттуда

## Лицензии
- Модели: Apache-2.0 (Wan) / MIT (GGUF-репаки)
- ComfyUI: GPL-3.0
- Real-ESRGAN: BSD-3-Clause

Не требуется аккаунт/токен HuggingFace — все зеркала публичные.