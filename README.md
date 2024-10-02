# qlyuker (клюкер)
Автоматизация клюкинга qlyuker.io

## Шаги для автоматизации клюкинга
1. Открой https://t.me/qlyukerbot/ в Telegram Web
2. Запусти WebApp
3. Открой devtools браузера
4. Вставь следующий код в консоль и отправь его 
```javascript
const iframes = document.querySelectorAll('iframe');
iframes.forEach(iframe => {
  let src = iframe.src;
  if (src.includes('qlyuker.io')) {
      if (src.includes('tgWebAppPlatform=weba')) {
      src = src.replace('tgWebAppPlatform=weba', 'tgWebAppPlatform=ios');
    }
    console.log('qlyuker.io auth url: ', src);
  }
}); 
```
5. Открой полученный url в новой вкладке
6. Открой devtools и переключись на мобильный режим просмотра
7. Перезагрузи страницу
8. Отправь следующий код для автоматического клюкинга в консоль
```javascript
function syncGameData(currentEnergy, taps) {
    const url = '/api/game/sync';
    const payload = {
        clientTime: Math.floor(Date.now() / 1000),
        currentEnergy: currentEnergy,
        taps: taps
    };
    fetch(url, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(payload)
    })
    .then(response => response.json())
    .then(data => {
        console.log('Response:', data);
    })
    .catch(error => {
        console.error('Error:', error);
    });
}
const interval = 30 * 1000;
setInterval(() => {
    syncGameData(0, 5000); // 5к тапов каждые 30 секунд
}, interval);
```
9. Не забывай постепенно покупать больше бустов энергии

## Пасхалка :)
Проделай шаги выше и отправь в консоль следующий код
```javascript
syncGameData(-9993945345345345, -9993945345345345);
```

